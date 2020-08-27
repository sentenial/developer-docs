---
title: Mutual TLS
keywords: MTLS
summary: "Mutual TLS Support allows for 2-way authentication between Nuapay and its clients, with both parties authenticating each other at the same time. "
sidebar: sec_sidebar
permalink: np_secmtls.html
folder: prodSecurity
---

## About Mutual TLS

In an MTLS connection: 

* The Nuapay API consumer (i.e the partner or merchant) and the Nuapay server, receiving that API message, participate in Mutual TLS. 
* The certificates prove the identity of each server to the other. 

MTLS is especially useful if you are deployed in the cloud and your source IP addresses are subject to change.

## MTLS Configuration

{% include note.html content="If you would like to use MTLS when passing you API requests please discuss your requirements with your Account Manager. " %}

In order to configure MTLS for you, Nuapay Support staff will:

* Request your certificate.
* Enable MTLS against your profile.

Note that once configured the certificate details provided in the API request headers must match the certificate details stored against your configuration. If the details do not match then your request will return a `403` HTTP Response.

