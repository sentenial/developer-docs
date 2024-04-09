---
title: Request Application Tokens
keywords: Request Token for Applications
summary: "The Request Token RESTful API allows you to generate a token for a specific application resource."
sidebar: tok_sidebar
permalink: tok_reqtokapp.html
folder: prodTokenMgmt
toc: true
---

## API Details

Use the Request Application Access Token Endpoints to generate an OAuth token which represents access for:
* A specific resource.
* A set of scopes.

## Application Friendly Tokens

Application Friendly Tokens:
* Can be used by Mobile Apps to call our APIs directly.
* As mobile apps are not considered a safe processing environment for credentials, the tokens will be limited to must-have access scopes that are required to deal with an individual resource.
* In most cases these will be used for API calls in read-only mode.

{% include tip.html content="If you use an application token against the wrong resource, you will be presented with a `401 unauthorized` response." %}

The image below illustrates the flow:

{% include image.html file="tok_app_tokens.png" url="images/tok_app_tokens.png" target = "_new" %}

Note that:

*	No IP Filtering is applied.
*	You will not be able to create resources using an application friendly token.
*	Calls contribute to your throttling statistics.
*	All resource creation is still a server-to-server call.
*	These tokens are available for the products listed below.

## Supported Applications

Application tokens may be generated for resources on any one of the following applications:

* `open_banking_pis`
* `open_banking_ais`
* `direct_debits`
* `credit_transfers`
* `accounts_validation_and_enrichment`
* `accounts`
* `nuapay_accounts`
* `emandates`
* `account_verification`


{% include swagger_gk.html %}

{% include urls-ob.html %}

## Request an Application Access Token

Use this service to retrieve a token that represents a resource.

<ul id="profileTabs1" class="nav nav-tabs">
</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');   
var timerRef1 = setInterval(function() { getDocs('operation/requestApplicationTokenUsingPOST','#profileTabs1',timerRef1); }, 500);
</script>
</div>
</div>

## Request an Application Access Token at the Organisation level

Use this service if you are interacting with Nuapay as a `merchant` and want to generate an application token at the merchant level.

<ul id="profileTabs4" class="nav nav-tabs">
</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');   
var timerRef4 = setInterval(function() { getDocs('operation/requestApplicationTokensForOrganisationUsingPOST','#profileTabs4',timerRef4); }, 500);
</script>
</div>
</div>


{% include links.html %}
