---
title: Token Management
keywords: Token Management Revocation
summary: "Revoke individual tokens based on a unique identifier or revoke all tokens linked to a specific merchant."
sidebar: em_sidebar
permalink: em_tokenmgmt.html
folder: prodEmandates
toc: true
---

## Overview

As outlined in [Partner Integration](em_partnerintegration.html), before you, as a partner, can initiate any API requests on behalf of your merchants, you must first generate an OAuth token unique to a specified merchant.  

Along with offering the service to `Request Access Token for Organisation`, a number of other endpoints are available to allow you to revoke OAuth tokens, which are described in the following sections.

<div markdown="span" class="alert alert-info" role="alert"><i class="fab fa-github"></i> <b>Swagger Reference:</b>
[Gatekeeper](https://github.com/sentenial/gatekeeper-swagger){:target="_blank"}</div>


{% include urls.html %}

## Revoke a Token for an Organisation

Use this service if you want to revoke a token for a specific `encodedOrganisationId` and `tokenId`

<ul id="profileTabs" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');   
var timerRef = setInterval(function() { getDocs('operation/revokeTokenForOrganisationUsingPOST','#profileTabs',timerRef); }, 500);
</script>
</div>
</div>

## Revoke a Token with a Token Identifier

Use this service to revoke a token by passing its `tokenId`

<ul id="profileTabs2" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef2 = setInterval(function() { getDocs('operation/revokeTokenUsingPOST','#profileTabs2',timerRef2); }, 500);
</script>
</div>
</div>


## Revoke All Tokens 

This service allows you to revoke all the tokens generated against a specific merchant (by passing the `encodedOrganisationId`).

<ul id="profileTabs3" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}

var timerRef3 = setInterval(function() { getDocs('operation/revokeTokensForOrganisationUsingPOST','#profileTabs3',timerRef3); }, 500);
</script>
</div>
</div>

## Revoke All Tokens for the Current Organisation

Use this service if you want to revoke all the tokens for the requesting organisation.

<ul id="profileTabs4" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}


var timerRef4 = setInterval(function() { getDocs('operation/revokeAllTokensUsingPOST','#profileTabs4',timerRef4); }, 500);
</script>
</div>
</div>

{% include links.html %}






