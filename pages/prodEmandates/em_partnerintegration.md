---
title: Partner Integration
keywords: Partner Integration
summary: "Partner integrations require you to retrieve an OAuth access token for a specific merchant and use that unique token in all subsequent API calls."
sidebar: em_sidebar
permalink: em_partnerintegration.html
folder: prodEmandates
toc: true
---

## OAuth Token Generation 

In order to initiate API requests on behalf of your merchants, you will first need to retrieve OAuth tokens.
The process is illustrated below:

<img src="images/partner_integration.png">

The Nuapay Customer Support team will issue An API Key to you upon request.
The OAuth token retrieved from the `/tokens` endpoint allows you to then generate API requests <b>on behalf of</b> a specific merchant/organisation.

When generating an API request, provide the retrieved token as the authentication username in all your API requests. 
A password is not required, however the request must be made from an allowed IP address.

|API authentication header format:|`Authorization: Bearer <OAuth Token>`|


## API Details - GET /organisations

<div markdown="span" class="alert alert-info" role="alert"><i class="fab fa-github"></i> <b>Swagger Reference:</b>
[Gatekeeper](https://github.com/sentenial/gatekeeper-swagger){:target="_blank"}</div>



Use the `/organisations` endpoint to retrive the organisations linked to your partner entity:


<ul id="profileTabs" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/ListOrganisationsUsingGET','#profileTabs',timerRef); }, 500);
</script>
</div>
</div>


## Scopes and Time To Live (TTL)

Before generating an OAuth token for a specific organisation you will need to specify the scopes required and the token's TTL.

At least one scope must be included in your request.

The TTL by default is 10 seconds but long-lived tokens may also be created by configuring the `expiresIn` value in the request body.

{% include note.html content="Where you have created a long-lived token, it is possible to revoke it through a revoke API request. See [Token Management](em_tokenmgmt.html) " %}


## API Details - POST /tokens

The `/organisations/{encodedOrganisationId}/tokens` endpoint takes an encoded organisation ID (returned from the `/organisations` endpoint) and returns an OAuth token. 

As outlined above, specify the `scopes` (required) and Time To Live - `expiresIn` (optional) in the request. 
Specify `admin` as the required scope when working with E-Mandates.


<ul id="profileTabs2" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef2 = setInterval(function() { getDocs('operation/requestTokensForOrganisationUsingPOST','#profileTabs2',timerRef2); }, 500);
</script>
</div>
</div>


Once you have retrieved the token for the required merchant, use it in the HTTP Authorization Header of the API requests you generate.


{% include links.html %}
