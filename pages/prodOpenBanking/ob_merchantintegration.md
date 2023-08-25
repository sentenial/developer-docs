---
title: Open Banking Merchant Integration
keywords: Merchant Integration Open Banking
summary: "Merchant integrations may use API Keys or OAuth tokens to secure access to the Open Banking APIs"
sidebar: ob_sidebar
permalink: ob_merchantintegration.html
folder: prodOpenBanking
toc: true
---


Two authentication approaches are available for merchant integrators, to ensure the security of your sensitive data, with both methods using Secure Sockets Layer (SSL) over the HTTPS protocol:

1. API Keys
1. OAuth Tokens

## API Key Authentication

Access to the API may be controlled by HTTP Basic authentication. For more on this, see the [API Key Authentication](np_secapikeyauth.html#api-key-authentication), under the Security section.


## Token Authentication

It is also possible to use OAuth tokens to secure your requests, rather than your API Key. OAuth Tokens offer greater flexibility to manage access to specific resources as they can be protected by Scopes. See [Token Authentication](np_secapikeyauth.html#token-authentication).

## Available Scopes

The following scopes are currently available:


|openbanking_pisp| Payment Initiation Service Provider access, restricted to retrieving ASPSP details and Payment initiation actions|
|openbanking_pisp_read| Payment Initiation Service Provider read access.|
|openbanking_aisp| Account Information Service Provider access, restricted to AISP functionality|
|openbanking_refund| Required to initiate refund payments|
|openbanking_refund_read| Required to retrieve a single refund transaction or to list refund payments.|
|openbanking_callback| Required to use the [Forward Payment Callback](ob_paymentcallback.html) service|


## Request Token

Specify the Time-to-Live value (`expiresIn`) and the required `scopes` in your request:


{% include swagger_gk.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/requestTokenUsingPOST','#profileTabs',timerRef); }, 500);


</script>


</div>
</div>




## Revoke Tokens

As mentioned earlier, for security reasons you may apply a specific time to live to your OAuth tokens or if required you may use the Revoke service to cancel any active tokens. It is possible to revoke a single token or revoke all tokens.

{% include urls.html %}


<ul id="profileTabs2" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs2', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');
var timerRef2 = setInterval(function() { getDocs('operation/revokeTokenUsingPOST','#profileTabs2',timerRef2); }, 500);


</script>



</div>
</div>


## Revoke ALL Tokens

{% include urls.html %}


<ul id="profileTabs3" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs3', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');
var timerRef3 = setInterval(function() { getDocs('operation/revokeAllTokensUsingPOST','#profileTabs3',timerRef3); }, 500);


</script>


</div>
</div>




{% include links.html %}
