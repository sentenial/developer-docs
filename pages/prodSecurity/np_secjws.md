---
title: JSON Web Signature
keywords: JSON Web Signature
summary: "JSON Web Signature"
sidebar: sec_sidebar
permalink: np_secjws.html
folder: prodSecurity
---

## About the JSON Web Signature

The 'JSON Web Signature' (JWS) is used as part of a REST header to validate requests made to certain endpoints ([Create Beneficiary](np_createbeneficiary.html) and [Create Credit Transfer](np_createct.html), for example).

Note that:

* Having this header indicates that you have signed the request with your private key.
* Any requests to the specific endpoints that require a JWS header, which do not include it, will fail.

{% include callout.html content="A JWS signature header is mandatory for specific requests for the purposes of non-repudiation. Where the JWS is required for a specific endpoint, this will be called out in the API description provided in this documentation. By providing a JWS signature you are ensuring that you, as merchant (or as a partner on behalf of a merchant), have generated the request; no other party has been involved; no tampering has occurred. While the JWS header is mandatory for Credit Transfer endpoints, it may also be used in all Nuapay endpoints if required." type="primary" %}

{% include tip.html content="To see how an example private key, certificate, JOSE header, request body and JWS work together, see the [JWS Signature Samples](np_secjwssample.html)." %}

## Steps Required to Generate a Valid Header

It is possible to configure your certificate via:

* The User Interface
* REST API.

{% include tip.html content="Partner users **must use the REST API approach**; Merchant users may use either the REST API or the User Interface method." %}

## User Interface Approach

To create a JOSE header **via the UI** you will need to:

* Log on to the Developer Dashboard.
* Generate a <b>Private Key</b> and a <b>Certificate</b>.
* Retrieve the certificate serial number and decode it.
* Extract the issuer details from your certificate.
* Use these details in your code to generate the JWS Signature when required.

{% include note.html content="If you do not already have access to the Developer Dashboard, please contact Nuapay support who will be happy to set you up and provide you with your logon credentials." %}


## REST Approach

To create a JOSE header **via REST** you will need to:

* Create a [Certificate Signing Request (CSR)](np_secjwsrest.html#creating-a-certificate-signing-request-csr).
* Pass that CSR in the [`POST/certificates`](np_secjwsrest.html#generating-your-certificate-via-rest) endpoint.
* Retrieve the certificate and extract the issuer details.
* Use these details in your code to generate the JWS Signature when required.

{% include tip.html content="The JWS Signature Generator tool (see the [JWS Signature Samples](np_secjwssample.html) section allows you to test that the JWS is working as expected. You will need to build logic into your application to generate a signature when required for specific payloads (typically for Credit-Transfer-related calls). For an example of how this might be done in Java, see the [JWS Sample Java](https://github.com/sentenial/jws-sample-java) on Nuapay Github." %}

## Setup Approaches

For more details on the configuration steps see:

* [JWS Configuration via UI](np_secjwsui.html) (for Merchants only)
* [JWS Configuration via REST](np_secjwsrest.html) (for Partners and Merchants)
