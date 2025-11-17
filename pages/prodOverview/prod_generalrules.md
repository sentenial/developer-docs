---
title: General API Rules
keywords: API General rules
summary: "The HTTPS protocol, API keys and originator configuration."
sidebar: productOverview_sidebar
permalink: prod_generalrules.html
folder: prodOpenBanking
---

<p>Note that all requests must:</p>

* Be sent via the HTTPS protocol
* Pass a specific encoded API Key or a unique OAuth token for authentication
* Originate from an allowed IP address (the allowed IP addresses will be configured for you when you register for the service)
* Include (at a minimum) the mandatory fields required for the specific request that is being made

<img src = 'images/api_gen_rules.png'>

{% include note.html content="Our API is backward-compatible. For more details see [Versioning and Backward Compatibility](prod_versioning.html)." %}

## Endpoints

All services may be accessed via the following URLs:

|SANDBOX|https://sandbox.nuapay.com/|
|PRODUCTION| https://api.nuapay.com/|

To request an API Key please contact our Support Team: <a href="mailto:api.support@nuapay.com">api.support@nuapay.com</a>.

## Response Handling

<p>All API requests generate responses.</p>

<p>Successful requests return one of the following:</p>

* 200 (<b>OK</b> - The request completed successfully)
* 201 (<b>Created</b> - A new resource has been created successfully)

{% include callout.html content="Response codes in the 400 to 499 range are generally related to business validation errors. Response codes in the 500 to 503 range are related to API service issues." type="primary" %}

See [HTTP Response Codes](em_httpreasons.html) for more information on the various responses and possible API error codes.

{% include links.html %}
