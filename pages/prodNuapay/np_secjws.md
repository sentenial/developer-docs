---
title: JSON Web Signature
keywords: JSON Web Signature
summary: "JSON Web Signature"
sidebar: np_sidebar
permalink: np_secjws.html
folder: prodNuapay
---

## About the JSON Web Signature

The 'JSON Web Signature' (JWS) is used as part of a REST header to validate requests made to certain endpoints (Beneficiary creation and CT creation). Having this header indicates that you have signed the request with your private key. If you have not provided your private key then these calls will be unsuccessful. 

{% include callout.html content="We require that you use a JWS signature for these types of requests for the pusposes of non-repudiation. By providing a JWS signature you are ensuring that you, as merchant, have generated the request; no other party has been involved; no tampering has occurred.." type="primary" %} 


This section will deal with the generation of the JWS.

## Generating a JSON Web Signature - Step-by-step

<ol>
	<li value="1">Generate and download a private key and certificate using the Developer Dashboard, for details on how to do this see the <a href="np_secpkidevdashboard.html">PKI Management</a> page in this guide.</li>
	<li value="2">Obtain the certificate serial number by viewing the certificate details. This is stored as a hexadecimal number and will need to be decoded.</li>
	<p>
		<img src="images/ViewCertificate.png" />
	</p>
	<li value="3">Obtain the subject parameters from the certificate,</li>
	<p>
		<img src="images/viewCertificate2.PNG" />
	</p>
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
	<li value="4">The serial number and subject parameters will be used to create the Javascript Object Signing and Encryption (JOSE) header which must contain the following fields and is used in computing the JWS,</li>
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
	
   