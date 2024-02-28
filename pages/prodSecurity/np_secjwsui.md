---
title: JSON Web Signature UI Setup
keywords: JSON Web Signature Configuration via the UI
summary: "JSON Web Signature User Interface Configuration"
sidebar: sec_sidebar
permalink: np_secjwsui.html
folder: prodSecurity
---

It is possible to set up and manage the JWS via the User Interface (as described in this section) or alternatively, this may be done via [REST](np_secjwsrest.html).

## Generating the PKI Key and Certificate via the UI

{% include note.html content="You will require access to the Nuapay Console / Developer Dashboard to configure your PKI settings via the User Interface. See the [Nuapay Console Overview](prod_consoleoverview.html) for more details." %}

To generate your private key and certificate:

1. Navigate to the **PKI Management** screen on the Nuapay Console. (If you cannot see this as a menu option please contact your Account Manager - specific permissions must be enabled to allow you to access this section of the dashboard).
1. If this is the first time using this screen you will see a notification to say that no PKI key has been generated.
<img src = "images/01_PKI_Management.png">
1. Click <b>Generate PKI Key</b>. This will generate:
* Your Private Key
* A Signed certificate
1. You will be prompted to download your private key (in .key format):
<img src = "images/02_PKI_Management.png">

{% include important.html content="This will be the only time you will be able to download this key and we will not retain it on our servers. If you need to regenerate the key for any reason you will need to revoke the certificate (see below)." %}

{% include important.html content="Ideally you should generate your public private key pair in a HSM and present the CSR to be signed over the REST endpoints. The certificate creation UI in the developer dashboard is offered as a convience tool to you" %}

## Managing Certificates via the UI

Once you have generated your PKI Key you have two available actions, you can:

* <b>Download</b> the certificate in .crt format. .
* <b>Revoke</b> your active certificate. This will invalidate the active certificate and private key, and you will no longer be able to generate JSON Web Signatures with this key and certificate. You will need to generate a new private key and certificate.


## Retrieving Details from the Certificate

You need to extract certain details from your certificate:

1. Browse to where you downloaded your certificate (.CRT file) and double-click to view its details.
1. Locate the certificate serial number section of the certificate. This is stored as a hexadecimal number **and will need to be decoded**.

	 <img src="images/ViewCertificate.png" />

1. There are various tools available online to allow you to decode the haxadecimal value, see <a href = "https://www.rapidtables.com/convert/number/hex-to-decimal.html" target = "_blank">https://www.rapidtables.com/convert/number/hex-to-decimal.html</a> for example. (The decoded number is the <i>kid</i> value that you will need to generate your Header later). In the example above, `0094cf4671` is decoded as `2496611953`.
1. Next, locate the subject parameters from the certificate:

	 <img src="images/viewCertificate2.PNG" />

    <p>The following details are provided:</p>
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
				<td>a2av3py82w (for example)</td>
				<td>Common name, the merchant identifier.</td>
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

<p>You have now gathered everything you need from the Certificate.</p>

## JOSE Header
To generate the JOSE Header you will need the following:

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
				<b>Example Value</b>
			</td>
			<td>
				<b>Description</b>
			</td>
		</tr>
		<tr>
			<td>alg</td>
			<td>RS256</td>
			<td>Algorithm, always 'RS256'</td>
		</tr>
		<tr>
			<td>kid</td>
			<td>2496611953 (for example)</td>
			<td>Key&#160;ID, use the decoded certificate serial number (see Step 3 above).</td>
		</tr>
		<tr>
			<td>iat</td>
			<td>0</td>
			<td>Issued at, the current Unix Epoch timestamp (in milliseconds). Note: this cannot be a future-date timestamp.</td>
		</tr>
		<tr>
			<td>iss</td>
			<td>"C=GB, L=London, OU=Nuapay API, O=Nuapay, CN=a2av3py82w"</td>
			<td>Issuer, use the certificate subject parameters. </td>
		</tr>
		<tr>
			<td>b64</td>
			<td>false</td>
			<td>Base64 encoded payload, always 'false'</td>
		</tr>
		<tr>
			<td>crit</td>
			<td>"crit": [
    "iat",
    "iss",
    "b64"
  ]
</td>
			<td>Critical, always ["iat","iss","b64"]</td>
		</tr>
	</tbody>
</table>

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

## Detached Payload JWS

The JWS signature generated will need to have a detached payload (the payload is sent as normal in the POST request body but it is not included in the JWS).

A signed JWS encodes information in three parts separated by periods:

* A Header
* A Payload
* A Signature

<strong>'header.payload.signature' </strong>
<br/>
A JWS also supports a detached format that omits the payload from the JWS:
<br/>
<strong>'header..signature' </strong>
<br/>
<p>
When using a detached JWS, the payload is sent as normal in the body but it is not included in the JWS.
</p>
