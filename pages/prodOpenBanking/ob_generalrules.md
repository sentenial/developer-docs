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
* Pass a specific encoded API Key (for merchant integrations) or a unique OAuth token (for partner integrations), for authentication
* Originate from an allowed IP address (the allowed IP addresses will be configured for you when you register for the service)
* Include (at a minimum) the mandatory fields required for the specific request that is being made

## Endpoints

Open Banking services may be accessed via the following endpoints:

|SANDBOX|https://tpp-sandbox.nuapay.com/tpp-ui/|
|PRODUCTION| https://tpp.nuapay.com/tpp-ui/|

To request an API Key please contact our Support Team: <a href="mailto:api.support@nuapay.com">api.support@nuapay.com</a>.

## Integration Options

Nuapay provides integrations for individual merchants and for partners. 
* For merchants, generally an encoded API Key is passed as basic authorisation in all API calls (alternatively an OAuth token may be used)
* In the partner model, OAuth tokens, specific to individual merchants linked to that partner, are passed in each request. 

For more on this see the [Integration Overview](ob_integrationoverview.html).

{% include links.html %}
