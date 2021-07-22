---
title: JSON Web Signature
keywords: JSON Web Signature
summary: "JSON Web Signature"
sidebar: sec_sidebar
permalink: np_secjws.html
folder: prodSecurity
---

## About the JSON Web Signature

The 'JSON Web Signature' (JWS) is used as part of a REST header to validate requests made to certain endpoints (Beneficiary creation and CT creation, for example). 

Having this header indicates that you have signed the request with your private key. Any requests to these specific endpoints that do not include the Javascript Object Signing and Encryption (JOSE) header will fail.

{% include callout.html content="We require that you use a JWS signature for these types of requests for the purposes of non-repudiation. By providing a JWS signature you are ensuring that you, as merchant (or as a partner on behalf of a merchant), have generated the request; no other party has been involved; no tampering has occurred." type="primary" %} 

|See [JWS Signature Samples](np_secjwssample.html) for an example private key, certificate, JOSE header, request body and JWS.|

## Steps Required to Generate a Valid Header

It is possible to configure your certificate via: 

* The User Interface 
* REST API.

{% include tip.html content="Partner users must use the REST API approach; Merchant users may use either the REST API or the User Interface method." %} 

To create a JOSE header **via the UI** you will need to:

* Generate a <b>Private Key</b> and a <b>Certificate</b>.
* Retrieve the certificate serial number and decode it.
* Extract the issuer details from your certificate.
* Use the JWS Signature Generator to generate the JOSE header. 

To create a JOSE header **via REST** you will need to:

* Generate a CSR.
* Pass that CSR in the `POST/certificates`
* Use the JWS Signature Generator to generate the JOSE header.

Once created you can then use this header value in any APIs where it is required.

## Setup Approaches

For more details on the configuration steps see: 

* [JWS Configuration via UI](np_secjwsui.html) (for Merchants only) 
* [JWS Configuration via REST](np_secjwsrest.html)


