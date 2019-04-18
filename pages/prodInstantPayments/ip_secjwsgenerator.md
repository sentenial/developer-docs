---
title: JWS Signature Header Generator
keywords: JWS Generator Utility - Non-repudiation JWS signature header generator
summary: "JWS Generator Utility"
sidebar: ip_sidebar
permalink: ip_secjwsgenerator.html
folder: prodInstantPayments
toc: false
---

<p>To use the Generator tool below:</p>
 <ol>
 <li value="1">Edit the JWS Header section and update the following: <ol><li value="1">"kid" </li><li value="2">"iat"</li><li value="3">"iss"</li></ol></li>
 <li value="2">Paste the HTTP request body into the JWS Payload section (JSON)</li>
 <li value="3">Paste the Private Key into the Private Key area (see <a href="ip_security.html#pki-management">PKI Management</a> for details of how to generate your Private Key).</li>
 <li value="4">Click the <b>Generate JWS Signature</b> button.</li>
 <li value="5">Use the generated string as a JWS-Signature header value when making your calls to the Sentenial Instant Payment Endpoint you referenced in step 2 above.</li>
 </ol>

## Generator Tool

Paste the required information as indicated below and click **Generate JWS Signature** when you're done:

{% include jws-signature-generator-ip.html %}

{% include links.html %}