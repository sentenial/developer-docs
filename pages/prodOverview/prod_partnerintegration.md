---
title: Partner Integration
keywords: Partner Integration
summary: "Partner integrations require you to retrieve an OAuth access token for a specific merchant and use that unique token in all subsequent API calls."
sidebar: productOverview_sidebar
permalink: prod_partnerintegration.html
folder: prodOverview
toc: true
---

## OAuth Token Generation

In order to initiate API requests on behalf of your merchants, you will first need to retrieve OAuth tokens.
The process is illustrated below:

<img src="images/partner_integration.png">

* The Nuapay Customer Support team will issue an API Key to you upon request or you may generate your own API Key via the [Nuapay Console](prod_consoleapi.html).
* The OAuth token retrieved from the `/tokens` endpoint allows you to then generate API requests <b>on behalf of</b> a specific merchant/organisation.
* When generating an API request, provide the retrieved token as the authentication username in all your API requests.
* A password is not required, however the request must be made from an allowed-IP-address.

|API authentication header format:|`Authorization: Bearer <OAuth Token>`|

## Scopes and Time To Live (TTL)

Before generating an OAuth token for a specific organisation you will need to specify the scopes required and the token's TTL.

At least one scope must be included in your request.

The TTL by default is 10 seconds but long-lived tokens may also be created by configuring the `expiresIn` value in the request body.

{% include note.html content="Where you have created a long-lived token, it is possible to revoke it through a revoke API request. See [Token Management](ob_tokenmgmt.html) " %}


## API Details - GET /organisations

<div markdown="span" class="alert alert-info" role="alert"><i class="fab fa-github"></i> <b>Swagger Reference:</b>
[Organisation](https://github.com/sentenial/organisation-swagger){:target="_blank"}</div>

{% include urls.html %}


Use the **GET** `/organisations` endpoint to retrive the organisations linked to your partner entity:


<ul id="profileTabs" class="nav nav-tabs">
</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/organisation-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listChildOrganisationsUsingGET','#profileTabs',timerRef); }, 500);
</script>
</div>
</div>

Use the returned Organization identifier to [Request a Token](tok_reqtokorg.html).




{% include links.html %}
