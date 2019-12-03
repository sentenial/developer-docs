---
title: Merchant Integration
keywords: Merchant Integration Open Banking
summary: "Merchant integrations may use API Keys or OAuth tokens to secure access to the Open Banking APIs"
sidebar: ob_sidebar
permalink: ob_merchantintegration.html
folder: prodNuapay
toc: true
---


Two authentication approaches are availbale for merchant integrators, to ensure the security of your sensitive data, with both methods using Secure Sockets Layer (SSL) over the HTTPS protocol:

1. API Keys 
1. OAuth Tokens

## API Key Authentication

Access to the API is controlled by HTTP Basic authentication.

{% include callout.html content="An API Key will be issued to you when you are onboarded. Also as part of the onboarding process, you will be required to provide the Onboarding team with a list of allowed IP addresses. This is essentially a white list of IP addresses for your business. Any API requests **not** originating from one of the white-listed IP addresses will be rejected." type="primary" %}


When generating an API request, provide your API key as the basic authentication username, encoded in Base64 in all your API requests. 
A password is not required, however the request must be made from an allowed IP address.

|API authentication header format:|`Authorization: Basic Base64(<API_Key>:)`|

**API Key Example**

To generate an encoded, Base64 HTTP Header ("Authorization: Basic {Base64(API_KEY:)}") for use in your requests:

* With the following given `APIKey = bb09c2b6a9478720765c757a8bcadf1aa1fb31554566a21118c9c75e26c29686`
* Encode this in base 64: `bb09c2b6a9478720765c757a8bcadf1aa1fb31554566a21118c9c75e26c29686:` (note that the colon (:) is required)
* the HTTPS header will then be: `"Authorization: Basic YmIwOWMyYjZhOTQ3ODcyMDc2NWM3NTdhOGJjYWRmMWFhMWZiMzE1NTQ1NjZhMjExMThjOWM3NWUyNmMyOTY4Njo="`

{% include note.html content="All API requests must be made over HTTPS; calls made over plain HTTP will fail. Note too that all API requests must be authenticated." %}


## Token Authentication

It is also possible to use OAuth tokens to secure your requests, rather than your API Key. 

OAuth Tokens offer greater flexibility to manage access to specific resources as they can be protected by Scopes. 

This is useful, for example, where you may want to give an engineer access to work with the Create Payment service but due to security concerns, you may not want that user to have access to the Refund service. 

Similarly, you may have outsourced some development expertise and you want to grant access to a service for only a period of time until the outsourced work is complete. An OAuth token can be configured with a Time-to-Live of 2 weeks for example, after which point it cannot be used. If you were to provide your API key to the outsourced resource in this scenario, then effectively that 3rd-party developer could still interact with Open Banking services via your API Key (even after completing their contracted work for you).

## Available Scopes

The following scopes are currently available:


|openbanking_pisp|Payment Initiation Service Provider access, restircted to retrieving ASPSP details and Payment initiation actions|
|openbanking_aisp|Account Information Service Provider access, restricted to AISP functionality|
|admin|All AISP and PISP functionality is available, at merchant level|
|bankadmin|All AISP and PISP functionality is available, at partner level|

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
