---
title: Request Organisation Tokens
keywords: Request Token (for Organization) Merchant and Partner users
summary: "The Request Token RESTful API allows you to generate a token for a specific organization (for Partners) or may be used to exchange an API Key for an access token (for merchants)."
sidebar: tok_sidebar
permalink: tok_reqtokorg.html
folder: prodTokenMgmt
toc: true
---

## API Details

Use the Request Access Endpoints to generate an OAuth token which represents access for:
* A specific Organization (for partner users).
* A set of scopes.
* With a defined expiry time.

It is possible to request a token in two modes, as a:

1. `Partner` user ("parent" entity), who is requesting a token on behalf of a "child" `Merchant` organization.
1. `Merchant` user who is requesting a token for the current (merchant) entity.


{% include swagger_gk.html %}

{% include urls-ob.html %}

## Request an Access Token for an Organisation

Use this service if you are a `partner` who wants to create a token for a specific `merchant` entity, which exists under your partner.

<ul id="profileTabs1" class="nav nav-tabs">
</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');   
var timerRef1 = setInterval(function() { getDocs('operation/requestTokensForOrganisationUsingPOST','#profileTabs1',timerRef1); }, 500);
</script>
</div>
</div>

## Request Access at the Organisation level

Use this service if you are interacting with Nuapay as a `merchant` and want to exchange your `API Key` for an access token.

<ul id="profileTabs4" class="nav nav-tabs">
</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');   
var timerRef4 = setInterval(function() { getDocs('operation/requestTokenUsingPOST','#profileTabs4',timerRef4); }, 500);
</script>
</div>
</div>


{% include links.html %}
