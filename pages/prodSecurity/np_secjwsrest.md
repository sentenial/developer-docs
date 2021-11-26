---
title: JSON Web Signature Configuration via REST
keywords: JSON Web Signature
summary: "JSON Web Signature"
sidebar: sec_sidebar
permalink: np_secjwsrest.html
folder: prodSecurity
---

{% include tip.html content="It is possible to set up and manage the JWS via REST (as described in this section) or alternatively, this may be done via the [Nuapay User Interface](np_secjwsui.html) through the Developer Dashboard. Partner users MUST use the REST approach." %}

## Creating a Certificate Signing Request (CSR)

Before you can create a certificate you must first generate a CSR.
When generating your CSR you must provide the following details:

<table style="width: 100%;mc-table-style: url('Resources/TableStyles/Simple.css');" class="TableStyle-Simple" cellspacing="0">
		<col style="width: 101px;" class="TableStyle-Simple-Column-Column1" />
		<col style="width: 198px;" class="TableStyle-Simple-Column-Column1" />
		<col style="width: 1140px;" class="TableStyle-Simple-Column-Column1" />
		<tbody>
			<tr>
				<td>
					<b>Attribute</b>
				</td>
				<td>
					<b>Value</b>
				</td>
				<td>
					<b>Description</b>
				</td>
			</tr>
			<tr>
				<td>OU</td>
				<td>Nuapay API</td>
				<td>Organization unit, this will always be 'Nuapay API' for certificates signed by Nuapay.</td>
			</tr>
			<tr>
				<td>CN</td>
				<td>example: a2av3py82w</td>
				<td>Common name; the merchant/partner identifier. If you don't have this identifier, please contact Nuapay Support.</td>
			</tr>
			<tr>
				<td>O</td>
				<td>Nuapay</td>
				<td>Organization, will always be 'Nuapay' for certificates signed by Nuapay.</td>
			</tr>
			<tr>
				<td>L</td>
				<td>London</td>
				<td>Locality, will always be 'London' for certificates signed by Nuapay.</td>
			</tr>
			<tr>
				<td>C</td>
				<td>GB</td>
				<td>Country Name, two letter country code will always be 'GB' for certificates signed by Nuapay.</td>
			</tr>
		</tbody>
	</table>

{% include important.html content="The State attribute is not required. If you want to provide it, or if it is required in the CSR-generation software that you are using, ensure that you reference its value as ST in the iss section of your JWS Header."%}

{% include callout.html content="The process for creating a CSR varies depending on the Web Server being used and it is not possible to cover all the variations in this documentation. Details are available online for all popular Web Servers." type="primary" %}

The Common Name `CN` may be either:
* A single **merchant identifier**
* Or it may be the **partner identifier**.

Where a partner identifier is used, the Certificate that is generated will be used to generate the JOSE header that will be used by that partner when calling API services (where non-repudiation is required) on behalf of its merchants.

Please contact Nuapay Support if you do not know your Nuapay merchant/partner identifier.

<br/>
## Detached Payload JWS
A signed JWS encodes information in three parts separated by periods:
<ul>
 <li>a header</li>
 <li>a payload</li>
 <li>a signature</li>
</ul>
<strong>'header.payload.signature' </strong>
<br/>
A JWS also supports a detached format that omits the payload from the JWS:
<br/>
<strong>'header..signature' </strong>
<br/>
<p>
When using a detached JWS, the payload is sent as normal in the body but it is not included in the JWS.
</p>



## Generating Your Certificate via REST

To generate your certificate via REST:

1. Call the `POST/certificates` endpoint.
1. Provide your CSR in the request.
1. A successful 201 reponse will return your certificate details.


{% include swagger_gk.html %}

<ul id="profileTabs1" class="nav nav-tabs">



</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');
var timerRef1 = setInterval(function() { getDocs('operation/generateUsingPOST','#profileTabs1',timerRef1); }, 500);


</script>


</div>
</div>


## Retrieving Details from the Certificate

In order to generate the JOSE Header you'll need to extract certain details from your certificate:

1. Copy the `cert` returned in the response (as described above) and paste it into a text file.
1. Replace the `\n` characters in the certificate with a new line character:
<img src = "images/sec_cert_newLine.png">
1. Save the file as a .crt.
1. Double-click this file to view its details.
1. Locate the certificate serial number section of the certificate. This is stored as a hexadecimal number and will need to be decoded.

   <img src="images/ViewCertificate.png">
1. There are various tools available online to allow you to decode the hexadecimal value, see <a href = "https://www.rapidtables.com/convert/number/hex-to-decimal.html" target = "_blank">https://www.rapidtables.com/convert/number/hex-to-decimal.html</a> for example. (The decoded number is the <i>kid</i> value that you will need to generate your signature later). In the example above, <b>0094cf4671</b> is decoded as <b>2496611953</b>.
1. Next, locate the subject parameters from the certificate:

	 <img src="images/viewCertificate2.PNG">

The following details are required:

|**Attribute**	|**Value**	|**Description**																							|
|OU				|Nuapay API	|Organization unit: this will always be 'Nuapay API' for certificates signed by Nuapay.						|
|CN				|a2av3py82w (Example)|Common name: the merchant/partner identifier.|
|O				|Nuapay		|Organization: will always be 'Nuapay' for certificates signed by Nuapay.									|
|L				|London		|Locality: will always be 'London' for certificates signed by Nuapay.										|
|C				|GB			|Country Name: two letter country code will always be 'GB' for certificates signed by Nuapay.				|

|Only the CN will vary per merchant/partner; all other attributes are static.|

The following are the details you need to generate the JOSE Header:

|**Attribute**|**Value**|**Description**|
|alg|RS256|Algorithm: always 'RS256'|
|kid|2496611953 (Example)| Key ID: use the decoded certificate serial number|
|iat|0|Issued at: always '0'|
|iss|"C=GB, L=London, OU=Nuapay API, O=Nuapay, CN=a2av3py82w"|Issuer: use the certificate subject parameters|
|b64|false|Base64 encoded payload: always 'false'|
|crit|["b64","iat","iss"]|Critical: always ["b64","iat","iss"]|

At this point you have the following unique details:
1. Your Private Key.
1. The Key ID (kid): the serial number from your .crt file.
1. The Common Name (CN): the Nuapay identifier for your merchant or partner entity.
(Other certificate elements are always the same i.e. the `C`, `OU`, `L`, etc. )

Use these details to generate your signature.

## Unit Testing

We recommend that you create a unit test that takes your inputs (as described above) and generates an appropriate JWS Signature.
To better understand how best to do this please refer to the:

* Java sample project: [https://github.com/sentenial/jws-sample-java](https://github.com/sentenial/jws-sample-java)
	 OR
* [JWS Signature Sample values](np_secjwssample.html) to see how a specific Private Key, Certificate and payload, can be used to generate a specific JWS signature (using the JWS Generator tool). You can then use the tool to pass in **YOUR** private key and certificate details to generate a signature for testing purposes.

{% include note.html content="Once enabled on Production, the Signature needs to be dynamically generated each time you create a request that require the JWS signature as a header e.g. for [Create Beneficiary](np_createbeneficiary.html), or [Create Credit Transfer](np_createct.html). The payload used in the JWS signature generation must match exactly the payload in your request." %}


## Managing Certificates

It is possible to List and Delete Certificates:

## List All Certificates

<ul id="profileTabs2" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');
var timerRef2 = setInterval(function() { getDocs('operation/listUsingGET','#profileTabs2',timerRef2); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

## Delete a Certificate

<ul id="profileTabs3" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');
var timerRef3 = setInterval(function() { getDocs('operation/deleteUsingDELETE','#profileTabs3',timerRef3); }, 500);


</script>


</div>
</div>
