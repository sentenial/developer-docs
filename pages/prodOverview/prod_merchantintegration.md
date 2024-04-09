---
title: Merchant Integration
keywords: Merchant Integration
summary: "Merchant integrations may use API Keys or OAuth tokens to secure access to the Nuapay APIs"
sidebar: productOverview_sidebar
permalink: prod_merchantintegration.html
folder: prodOverview
toc: true
---


Two authentication approaches are available for merchant integrators, to ensure the security of your sensitive data, with both methods using Secure Sockets Layer (SSL) over the HTTPS protocol:

1. API Keys
1. OAuth Tokens

## API Key Authentication

Access to the API is controlled by HTTP Basic authentication.

{% include callout.html content="An API Key will be issued to you when you are onboarded or you may generate your own via the [Nuapay Console](prod_consoleapi.html). Also as part of the onboarding process, you will be required to provide the Onboarding team with a list of allowed IP addresses (or configure these yourself - see [Allowed-IP Configuration](prod_consoleapi.html#allowed-ips-configuration)). This is a white list of IP addresses for your business. Any API requests **not** originating from one of the white-listed IP addresses will be rejected." type="primary" %}


When generating an API request:
* Provide your API key as the basic authentication username, **encoded in Base64** in all your API requests.
* A password is not required, however the request must be made from an allowed IP address.

|API authentication header format:|`Authorization: Basic Base64(<API_Key>:)`|

## Example

To generate an encoded, Base64 HTTP Header ("Authorization: Basic {Base64(API_KEY:)}") for use in your requests:

* With the following given `APIKey = bb09c2b6a9478720765c757a8bcadf1aa1fb31554566a21118c9c75e26c29686`
* Encode this in base 64: `bb09c2b6a9478720765c757a8bcadf1aa1fb31554566a21118c9c75e26c29686:` (note that the colon (:) is required)
* the HTTPS header will then be: `"Authorization: Basic YmIwOWMyYjZhOTQ3ODcyMDc2NWM3NTdhOGJjYWRmMWFhMWZiMzE1NTQ1NjZhMjExMThjOWM3NWUyNmMyOTY4Njo="`

{% include note.html content="All API requests must be made over HTTPS; calls made over HTTP will fail. Note too that all API requests must be authenticated." %}

## Token Authentication

* It is also possible to use OAuth tokens to secure your requests, rather than your API Key.
* OAuth Tokens offer greater flexibility to manage access to specific resources as they can be protected by Scopes.
* See [Token Authentication](np_secapikeyauth.html#token-authentication) for more details.

Note that it is possible to carry out the following operations, as described in the [Token Management](tok_tokenmgmt.html) section:

* [Request Tokens](tok_reqtokorg.html#request-access-at-the-organisation-level)
* [Revoke a Token](tok_revoke.html#revoke-a-token-for-an-organisation-with-a-token-id)
* [Revoke all Tokens](tok_revoke.html#revoke-all-tokens-for-the-current-organisation)


{% include links.html %}
