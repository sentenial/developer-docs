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
