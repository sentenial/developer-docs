---
title: Security Overview
keywords: Security Overview Open Banking
summary: "Because you are working with sensitive financial data, we ensure that our Nuapay API is highly secure."
sidebar: ob_sidebar
permalink: ob_secoverview.html
folder: prodNuapay
toc: false
---


We use API Keys to ensure the security of your sensitive data, which is transmitted via Secure Sockets Layer (SSL) over the HTTPS protocol.

## API Key Authentication

Access to the API is controlled by HTTP Basic authentication.

Provide your API key as the basic authentication username, encoded in Base64. No password needs to be provided, however the request must be made from an allowed IP address configured in Nuapay.

API authentication header format:

`Authorization: Basic Base64(<API_Key>:)`

All API requests must be made over HTTPS, calls made over plain HTTP will fail. All API requests must be authenticated.

For REST authentication the following HTTP headers in each HTTP request targeted are required:


1. template: "Authorization: Basic {Base64(API_KEY:)}"
1. example
1. * With the following given `APIKey = bb09c2b6a9478720765c757a8bcadf1aa1fb31554566a21118c9c75e26c29686`
1. * We encode this in base 64: `bb09c2b6a9478720765c757a8bcadf1aa1fb31554566a21118c9c75e26c29686:` (note that the colon (:) is required)
1. * the HTTPS header will then be: `"Authorization: Basic YmIwOWMyYjZhOTQ3ODcyMDc2NWM3NTdhOGJjYWRmMWFhMWZiMzE1NTQ1NjZhMjExMThjOWM3NWUyNmMyOTY4Njo="`


{% include links.html %}
