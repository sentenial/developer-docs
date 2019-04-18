---
title: Security
keywords: Inbound Instant Payment Security API Key JWS Web Signature
summary: "Your Instant Payments are safe; learn more about how we manage security here."
sidebar: ip_sidebar
permalink: ip_security.html
folder: prodInstantPayment
toc: true
---
 
We use API Keys to ensure the security of your sensitive data, which is transmitted via Secure Sockets Layer (SSL) over the HTTPS protocol.

## API Key Authentication

For REST authentication the following HTTP headers in each HTTP request targeted are required.

Mandatory API Key authentication basic:

1. Template: "Authorization: Basic {Base64(API_KEY:)}"
1. Example
   - With the following given APIKey = ``bb09c2b6a9478720765c757a8bcadf1aa1fb31554566a21118c9c75e26c29686``
   - We encode this in base 64: ``bb09c2b6a9478720765c757a8bcadf1aa1fb31554566a21118c9c75e26c29686:`` (note that the colon (:) is required)
   - the HTTPS header will then be: Authorization: Basic ``YmIwOWMyYjZhOTQ3ODcyMDc2NWM3NTdhOGJjYWRmMWFhMWZiMzE1NTQ1NjZhMjExMThjOWM3NWUyNmMyOTY4Njo=``




## PKI Management

PKI (Public Key Infrastructure) Management is used to generate a private key and signed certificate to be used in generating JSON Web Signatures (JWS) for non-repudiation in our REST endpoints.

To generate your private key and certificate:

* Log on to the Developer Dashboard.
* Navigate to the 'PKI Management' screen.
* If this is the first time using this screen the only button available to you will be **Generate PKI Key**.
* Click this button to generate your Private key and signed certificate.

<img src="images/01_PKI_Management_Generate.png">

Once you click the button you will be prompted to download your private key in .key format.

We recommend you store your private key in a secure location such as on a local or cloud based HSM.

{% include note.html content="This will be the only time you will be able to download this key and we will not retain it on our servers. If you need to regenerate the key for any reason you will need to revoke the certificate (see below)." %}

<img src="images/02_PKI_Management_Generate.png">

After closing the download dialog box you will see your active certificate and there are two actions you can carry out on it:

|**A**| You can download the certificate in .crt format. You will be required to do this to generate JSON Web Signature|
|**B**| You can revoke your active certificate. Note: This will invalidate the active certificate and private key, and you will no longer be able to generate JSON Web Signatures with this key and certificate. You will need to generate a new private key and certificate using the 'Generate PKI Key'|

<img src="images/03_PKI_Management_Generate.png">

## JSON Web Signature

The 'JSON Web Signature' (JWS) is used as part of a REST header to validate requests made to create an instant payment. Having this header indicates that you have signed the request with your private key. Any requests to this specific endpoint that does not include the Javascript Object Signing and Encryption (JOSE) header will fail.

{% include callout.html content="We require that you use a JWS signature for this requests for the pusposes of non-repudiation. By providing a JWS signature you are ensuring that you, as a client's financial institution partner, have generated the request; no other party has been involved; no tampering has occurred." type="primary" %}  


## Steps Required to Generate a Valid Header

To create a JOSE header you will need to:

* Generate a <b>Private Key</b> and a <b>Certificate</b> (as outlined above).
* Retrieve the certificate serial number and decode it.
* Extract the issuer details from your certificate.
* Use the JWS Signature Generator to generate the JOSE header. 

You will then use this header value in any APIs where it is required.  


## Retrieving Details from the Certificate

In order to generate the JOSE Header you'll need to extract certain details from your certificate:

<ol>
	<li value="1">Browse to where you downloaded your certificate (.CRT file) and double-click to view its details.</li>
	<li value="2">Locate the certificate serial number section of the certificate. This is stored as a hexadecimal number and will need to be decoded.</li>
	<p>
		<img src="images/ViewCertificateIP.png" />
	</p>
	<li value="3">There are various tools available online to allow you to decode the haxadecimal value, see <a href = "https://www.rapidtables.com/convert/number/hex-to-decimal.html" target = "_blank">https://www.rapidtables.com/convert/number/hex-to-decimal.html</a> for example. (The decoded number is the <i>kid</i> value that you will need to generate your Header later).</li> 
	<li value="4">Next, locate the subject parameters from the certificate:</li>
    
    <p>
		<img src="images/viewCertificateIP2.PNG" />
	</p>
    </ol>
    
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
				<td>Sentenial API</td>
				<td>Organization unit, this will always be 'Nuapay API' for certificates signed by Nuapay.</td>
			</tr>
			<tr>
				<td>CN</td>
				<td>a2av3py82w</td>
				<td>Common name, the originator technical ID</td>
			</tr>
			<tr>
				<td>O</td>
				<td>Sentenial</td>
				<td>Organization, will always be 'Sentenial' for certificates signed by Sentenial.</td>
			</tr>
			<tr>
				<td>L</td>
				<td>London</td>
				<td>Locality, will always be 'London' for certificates signed by Sentenial.</td>
			</tr>
			<tr>
				<td>C</td>
				<td>GB</td>
				<td>Country Name, two letter country code will always be 'GB' for certificates signed by Sentenial.</td>
			</tr>
		</tbody>
	</table>

<p>At this point you have gathered everything you need from the Certificate. These are the details you need to generate the JOSE Header: </p>			
<table>
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
				<td>"C=GB, L=London, OU=Sentenial API, O=Sentenial, CN=a2av3py82w"</td>
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
	
Use the [JWS Signature Generator](ip_secjwsgenerator.html) to generate the JOSE Header.


{% include links.html %}
