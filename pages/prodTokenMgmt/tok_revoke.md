---
title: Revoke Tokens
keywords: Revoke Tokens
summary: "It is possible to revoke all tokens at the organization level or revoke a specific token."
sidebar: tok_sidebar
permalink: tok_revoke.html
folder: prodTokenMgmt
toc: true
---

## API Details

Use this Endpoint to revoke an OAuth token. It is possible to revoke:
* All tokens for a specific Organization.
* A single token, by passing its `tokenId`

{% include swagger_gk.html %}

{% include urls-ob.html %}


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


## Revoke All Tokens for the Current Organisation

Use this service if you want to revoke all the tokens for the requesting organisation (i.e. at the `merchant` level).

<ul id="profileTabs4" class="nav nav-tabs">
</ul>

{% include redoc.html %}


var timerRef4 = setInterval(function() { getDocs('operation/revokeAllTokensUsingPOST','#profileTabs4',timerRef4); }, 500);
</script>
</div>
</div>

## Revoke a Token for the Current Organisation

Use this serivce to revoke a specific `tokenId`:

<ul id="profileTabs5" class="nav nav-tabs">
</ul>

{% include redoc.html %}


var timerRef5 = setInterval(function() { getDocs('operation/revokeTokenUsingPOST','#profileTabs5',timerRef5); }, 500);
</script>
</div>
</div>

{% include links.html %}
