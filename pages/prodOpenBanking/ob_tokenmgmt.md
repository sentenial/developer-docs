---
title: Token Management
keywords: Token Management Revocation
summary: "Revoke individual tokens based on a unique identifier or revoke all tokens linked to a specific merchant."
sidebar: ob_sidebar
permalink: ob_tokenmgmt.html
folder: prodOpenBanking
toc: true
---

## Overview

Token management is mandatory for partner users and optional for merchant users.

* As a partner, and as outlined in [Partner Integration](ob_partnerintegration.html), before you can initiate any API requests on behalf of a merchant, you must first generate an OAuth token representing that specified merchant.  
* As a merchant, following the [Merchant Integration](ob_merchantintegration.html), you may also want to authenticate with OAuth tokens rather than using an API Key.

The following sections offer a reference to all the available Token endpoints.

<div markdown="span" class="alert alert-info" role="alert"><i class="fab fa-github"></i> <b>Swagger Reference:</b>
[Gatekeeper](https://github.com/sentenial/gatekeeper-swagger){:target="_blank"}</div>

## Request an Access Token for an Organisation

Exchange an API Key to retrieve an OAuth access token for the originator/merchant.

<ul id="profileTabs1" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');   
var timerRef1 = setInterval(function() { getDocs('operation/requestTokensForOrganisationUsingPOST','#profileTabs1',timerRef1); }, 500);
</script>
</div>
</div>

## Revoke All Tokens for an Organisation

This service allows you to revoke all the tokens generated against a specific merchant (by passing the `encodedOrganisationId`).

<ul id="profileTabs2" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}

var timerRef2 = setInterval(function() { getDocs('operation/revokeTokensForOrganisationUsingPOST','#profileTabs2',timerRef2); }, 500);
</script>
</div>
</div>

## Revoke a Token for an Organisation (with a Token ID)

Use this service if you want to revoke a token for a specific `encodedOrganisationId` and `tokenId`

<ul id="profileTabs3" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');   
var timerRef3 = setInterval(function() { getDocs('operation/revokeTokenForOrganisationUsingPOST','#profileTabs3',timerRef3); }, 500);
</script>
</div>
</div>

## Request an Access Token ##

Use this service to exchange your API Key for a token.

<ul id="profileTabs4" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');   
var timerRef4 = setInterval(function() { getDocs('operation/requestTokenUsingPOST','#profileTabs4',timerRef4); }, 500);
</script>
</div>
</div>


## Revoke All Tokens for the Current Organisation

Use this service if you want to revoke all the tokens for the requesting organisation.

<ul id="profileTabs5" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}


var timerRef5 = setInterval(function() { getDocs('operation/revokeAllTokensUsingPOST','#profileTabs5',timerRef5); }, 500);
</script>
</div>
</div>


## Revoke a Token with a Token Identifier

Use this service to revoke a token by passing its `tokenId`

<ul id="profileTabs6" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef6 = setInterval(function() { getDocs('operation/revokeTokenUsingPOST','#profileTabs6',timerRef6); }, 500);
</script>
</div>
</div>






{% include links.html %}






