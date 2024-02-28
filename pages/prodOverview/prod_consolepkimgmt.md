---
title: Nuapay Console PKI Management
keywords: Nuapay Console PKI Management
summary: "Manage PKI via the Console."
sidebar: productOverview_sidebar
permalink: prod_consolewpkimgmt.html
folder: prodOverview
toc: false
---


The 'JSON Web Signature' (JWS) is used as part of a REST header to validate requests made to certain endpoints ([Create Beneficiary](np_createbeneficiary.html) and [Create Credit Transfer](np_createct.html), for example).

Note that:

* Having this header indicates that you have signed the request with your private key.
* Any requests to the specific endpoints that require a JWS header, which do not include it, will fail.

For more information on PKI and configuring your security, see the [Security Overview](np_secjws.html).

## PKI Configuration

In order to created a JWS you must first generate a private key via the PKI Configuration section of the Nuapay Console.

To access the PKI configuration:

1. Click **PKI Management** from the left-side menu:
<img src= "images/console_pki.png">
1. Click **Generate PKI Key** if you have not already created one.

See [Generating the PKI Key and Certificate via the UI](np_secjwsui.html#generating-the-pki-key-and-certificate-via-the-ui) for the full set of steps.



{% include links.html %}
