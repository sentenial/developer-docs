---
title: JWS Signature Header Generator
keywords: JWS Generator Utility - Non-repudiation JWS signature header generator
summary: "JWS Generator Utility"
sidebar: sec_sidebar
permalink: np_secjwsgenerator.html
folder: prodSecurity
toc: false
---

<p>To use the Generator tool below:</p>
 <ol>
 <li value="1">Edit the JWS Header section and update the following: <ol><li value="1">"kid" </li><li value="2">"iss" (COMMON NAME)</li></ol></li>
 <li value="2">Paste the HTTP request body into the JWS Payload section (JSON)</li>
 <li value="3">Paste the Private Key into the Private Key area (see <a href="np_secjws.html#generating-the-pki-key-and-certificate">Generating the PKI Key and Certificate</a> for details of how to generate your Private Key).</li>
 <li value="4">Click the <b>Generate JWS Signature</b> button.</li>
 <li value="5">Use the generated string as a JWS-Signature header value when making your call (passed in the Payload) to the Nuapay Endpoint you referenced in step 2 above.</li>
 </ol>

## Generator Tool

Paste the required information as indicated below:
* Your certificate serial number (kid)
* Your Commone Name (CN)
* Your JSON Payload
* Your Private Key

Click **Generate JWS Signature** when you're done:

{% include jws-signature-generator.html %}


## Automating the JWS
The Generator Tool allows you to create a JWS signature value based on your certificate details and private key and is intended for your initial testing.

1. Use the tool above to generate a JWS for a specific payload (e.g. for a [Create Beneficiary](np_createbeneficiary.html) request).
1. Copy the generated JWS and paste that as a header value in your `Create Beneficiary` call.
1. Generate your request and confirm that it is successful. Once your JWS is working as expected, you will need to code a solution that takes your certificate and private key to automatically generate a JWS and add it as a header to any requests that require it.

## Troubleshooting
If you are unsuccessful in creating a request with the generated JWS signature, please try the following:
* When generating the [CSR](np_secjwsrest.html#tag/Certificates) (If you are using REST to generate your certificate), ensure that you have not provided a value for State.
* Ensure that you are pasting the decoded Serial Number for the `kid` value in the Generation Tool (and not the raw hexadecimal value).
* Try to pass your request with an empty payload e.g. `{}` and check the error code returned.
  * If you receive a `7085: Beneficiary object is required` you will know that your JWS is working and the issue is with the request body.
  * A `7200` or a `7201` error will indicate that there is a JWS problem.
* If you have pretty-printed your request body and pasted it into the Generator tool, try removing any CR or LF characters and retry.
* Similarly if your payload was not pretty-printed when pasted into the Generation tool, ensure that it is not pretty-printed when calling the endpoint with the JWS Signature header.
* In the JWS Header section of the Generator above, ensure that you only paste your `kid` and `CN` values and that no extra spaces or formatting changes are applied. (Any change will result in an incorrect JWS being generated).
* Check the [JWS Signature Sample](np_secjwssample.html) page where an example private key, certificate, JOSE Header and Sample request are provided along with the generated JWS. (Try passing the values into the Generator tool above to confirm that that JWS is generated as expected) .

## Java Example

For an example of how signatures may be generated in Java, please see the following:
<a href = "https://github.com/sentenial/jws-sample-java" target= "new">https://github.com/sentenial/jws-sample-java</a>

{% include links.html %}
