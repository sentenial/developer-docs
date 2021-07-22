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

{% include note.html content="You will require access to the Developer Dashboard via the Nuapay front end. Once you have logged on to Nuapay, the <b>Developer Dashboard</b> link is available on the top right of the screen. Click this to launch the dashboard." %}

To generate your private key and certificate:

1. Navigate to the 'PKI Management' screen on the Developer Dashboard. (If you cannot see this as a menu option please contact your Account Manager - specific permissions must be enabled to allow you to access this section of the dashboard). 
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

In order to generate the JOSE Header you'll need to extract certain details from your certificate:

<ol>
	<li value="1">Browse to where you downloaded your certificate (.CRT file) and double-click to view its details.</li>
	<li value="2">Locate the certificate serial number section of the certificate. This is stored as a hexadecimal number and will need to be decoded.</li>
	<p>
		<img src="images/ViewCertificate.png" />
	</p>
	<li value="3">There are various tools available online to allow you to decode the haxadecimal value, see <a href = "https://www.rapidtables.com/convert/number/hex-to-decimal.html" target = "_blank">https://www.rapidtables.com/convert/number/hex-to-decimal.html</a> for example. (The decoded number is the <i>kid</i> value that you will need to generate your Header later).</li> 
	<li value="4">Next, locate the subject parameters from the certificate:</li>

    <p>
		<img src="images/viewCertificate2.PNG" />
	</p>
    <p>The following details are required:</p>
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
				<td>a2av3py82w</td>
				<td>Common name, the originator technical ID</td>
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



<p>At this point you have gathered everything you need from the Certificate. These are the details you need to generate the JOSE Header: </p>
	<table style="width" cellspacing="0">
		<col style="width: 103px;"  />
		<col style="width: 308px;" />
		<col style="width: 33%;"  />
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
				<td>alg</td>
				<td>RS256</td>
				<td>Algorithm, always 'RS256'</td>
			</tr>
			<tr>
				<td>kid</td>
				<td>2496611953</td>
				<td>Key&#160;ID, use the decoded certificate serial number</td>
			</tr>
			<tr>
				<td>iat</td>
				<td>0</td>
				<td>Issued at, always '0'</td>
			</tr>
			<tr>
				<td>iss</td>
				<td>"C=GB, L=London, OU=Nuapay API, O=Nuapay, CN=a2av3py82w"</td>
				<td>Issuer, use the certificate subject parameters</td>
			</tr>
			<tr>
				<td>b64</td>
				<td>false</td>
				<td>Base64 encoded payload, always 'false'</td>
			</tr>
			<tr>
				<td>crit</td>
				<td>["b64","iat","iss"]</td>
				<td>Critical, always ["b64","iat","iss"]</td>
			</tr>
		</tbody>
	</table>
<p>Use the <a href= "np_secjwsgenerator.html">JWS Signature Generator</a> to create the JOSE Header.</p>

{% include note.html content="The expected JWS should use a detached payload." %}

<br/>
<h1> Detached Payload JWS</h1>
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

