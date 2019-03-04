---
title: Merchant Integration
keywords: Merchant Integration 
summary: "Merchant integrations use API Keys to secure access to the Nuapay APIs"
sidebar: em_sidebar
permalink: em_merchantintegration.html
folder: prodEmandates
toc: false
---


For single merchant integrations, API Keys are used to ensure the security of your sensitive data, transmitted via Secure Sockets Layer (SSL) over the HTTPS protocol.

## API Key Authentication

Access to the API is controlled by HTTP Basic authentication.

{% include callout.html content="An API Key will be issued to you when you are onboarded. Also as part of the onboarding process, you will be required to provide the Onboarding team with a list of allowed IP addresses. This is essentially a white list of IP addresses for your business. Any API requests **not** originating from one of the white-listed IP addresses will be rejected." type="primary" %}


When generating an API request, provide your API key as the basic authentication username, encoded in Base64 in all your API requests. 
A password is not required, however the request must be made from an allowed IP address.

|API authentication header format:|`Authorization: Basic Base64(<API_Key>:)`|

## Example

To generate an encoded, Base64 HTTP Header ("Authorization: Basic {Base64(API_KEY:)}") for use in your requests:

* With the following given `APIKey = bb09c2b6a9478720765c757a8bcadf1aa1fb31554566a21118c9c75e26c29686`
* Encode this in base 64: `bb09c2b6a9478720765c757a8bcadf1aa1fb31554566a21118c9c75e26c29686:` (note that the colon (:) is required)
* the HTTPS header will then be: `"Authorization: Basic YmIwOWMyYjZhOTQ3ODcyMDc2NWM3NTdhOGJjYWRmMWFhMWZiMzE1NTQ1NjZhMjExMThjOWM3NWUyNmMyOTY4Njo="`

{% include note.html content="All API requests must be made over HTTPS; calls made over HTTP will fail. Note too that all API requests must be authenticated." %}


{% include links.html %}
