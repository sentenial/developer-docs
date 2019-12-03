---
title: General API Rules
keywords: API General rules Open Banking
summary: "The HTTPS protocol, API keys and originator configuration."
sidebar: ob_sidebar
permalink: ob_generalrules.html
folder: prodOpenBanking
---

<p>Note that all requests must:</p>

* Be sent via the HTTPS protocol
* Pass a specific encoded API Key or a unique OAuth token for authentication
* Originate from an allowed IP address (the allowed IP addresses will be configured for you when you register for the service)
* Include (at a minimum) the mandatory fields required for the specific request that is being made

{% include note.html content="Our API is backward-compatible. For more details see [Versioning and Backward Compatibility](prod_versioning.html) under the Product Overview section." %}

## Endpoints

Open Banking services may be accessed via the following URLs:

|SANDBOX|https://sandbox.nuapay.com/tpp/|
|PRODUCTION| https://api.nuapay.com/tpp/|

To request an API Key please contact our Support Team: <a href="mailto:api.support@nuapay.com">api.support@nuapay.com</a>.

## Integration Options

Nuapay provides integrations for individual merchants and for partners. 
* For merchants, generally an encoded API Key is passed as basic authorisation in all API calls (alternatively an OAuth token may be used)
* In the partner model, OAuth tokens, specific to individual merchants linked to that partner, are passed in each request. 

For more on this see the [Integration Overview](ob_integrationoverview.html).

{% include links.html %}
