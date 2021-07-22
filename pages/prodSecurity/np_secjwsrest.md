---
title: JSON Web Signature Configuration via REST
keywords: JSON Web Signature
summary: "JSON Web Signature"
sidebar: sec_sidebar
permalink: np_secjwsrest.html
folder: prodSecurity
---

It is possible to set up and manage the JWS via REST (as described in this section) or alternatively, this may be done via the [Nuapay User Interface](np_secjwsui.html) through the Developer Dashboard.

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
				<td>Common name, the merchant/partner technical ID</td>
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

{% include tip.html content="The State attribute is not required and **should not be included in your certficate**"%} 

{% include callout.html content="The process for creating a CSR varies depending on the Web Server being used and it is not poissible to cover all the variations in this documentation. Details are available online for all popular Web Servers." type="primary" %} 

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

<ul id="profileTabs1" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');
var timerRef1 = setInterval(function() { getDocs('operation/generateUsingPOST','#profileTabs1',timerRef1); }, 500);


</script>


</div>
</div>


## Managing Certificates 

It is possible to List and Delete Certificates:

## List

<ul id="profileTabs2" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');
var timerRef2 = setInterval(function() { getDocs('operation/listUsingGET','#profileTabs2',timerRef2); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

## Delete

<ul id="profileTabs3" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');
var timerRef3 = setInterval(function() { getDocs('operation/deleteUsingDELETE','#profileTabs3',timerRef3); }, 500);


</script>


</div>
</div>

