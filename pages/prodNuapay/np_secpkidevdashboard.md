---
title: PKI Management
keywords: PKI Management Security in Developer Dashboard
summary: "PKI Management in Developer Dashboard"
sidebar: np_sidebar
permalink: np_secpkidevdashboard.html
folder: prodNuapay
---

## Generating the PKI Key and Certificate

PKI (Public Key Infrastructure) Management is used to generate a private key and signed certificate to be used in generating JSON Web Signatures (JWS) for non-repudiation in certain REST endpoints.

To generate your private key and certificate:

1. Navigate to the 'PKI Management' screen on the Developer Dashboard. (If you cannot see this screen please contact your Account Manager - specific permissions must be enabled to allow you to access this section of the dashboard). 
1. If this is the first time using this screen you will see a notification to say that no PKI key has been generated. 
1. Click <b>Generate PKI Key</b>. This will generate:
* Your Private Key
* A Signed certificate

<img src = "images/01_PKI_Management.png">

You will be prompted to download your private key (in .key format):


<img src = "images/02_PKI_Management.png">

{% include important.html content="This will be the only time you will be able to download this key and we will not retain it on our servers. If you need to regenerate the key for any reason you will need to revoke the certificate (see below)." %}

## Managing the Certificate

Once you have generated a certficate you have two available actions, you can:

* <b>Download</b> the certificate in .crt format. You will be required to do this to generate a <a href ="np_secjws.html">JSON Web Signature</a>.
* <b>Revoke</b> your active certificate. Note: This will invalidate the active certificate and private key, and you will no longer be able to generate JSON Web Signatures with this key and certificate. You will need to generate a new private key and certificate using the 'Generate PKI Key'.


{% include links.html %}
	