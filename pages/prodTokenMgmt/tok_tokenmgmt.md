---
title: Token Management
keywords: Token Management
summary: "OAuth Tokens may be used to authorize your API requests. While this is optional for merchants (who may use an API Key), where you are operating as a Partner user, you must use tokens when processing requests on behalf of your child merchants."
sidebar: tok_sidebar
permalink: tok_tokenmgmt.html
folder: prodTokenMgmt
toc: true
---

## Overview

It is possible to use OAuth tokens as an alternative to `API Keys`, to access the Nuapay APIs. API Keys provide a straightforward way for applications to access APIs, but they have some limitations:

* They can be easily shared, which can lead to unauthorized access to your data.
* Additionally, if an API Key is compromised, it can be challenging to revoke access to it.
* There is also the danger that you could re-generate your API key in error, via the Developer Dashboard, which would result in you losing access to your Nuapay services.

OAuth tokens, provide a more secure and flexible way to authorize access to your data.
Tokens:

* Allow you to control exactly which resources an application can access and for how long.
* In addition, tokens can be easily revoked.

## OAuth Token Types

There are three token types:

* 'Partner' level
* 'Merchant' level
* 'Application' level

## When Do I Need to Use OAuth Tokens?

Token management is mandatory for partner users and optional for merchant users.

* As a `partner`, once you generate an OAuth token representing a specified merchant, you can initiate any API requests on behalf of that merchant.
* As a `merchant`, you may also want to authenticate with OAuth tokens rather than using an `API Key`.
* In addition to using OAuth tokens to represent a merchant entity, you may also use tokens for access to specific applications or resources. 

See the API section for details of the various Token endpoints.

{% include links.html %}
