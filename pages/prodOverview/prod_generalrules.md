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

{% include note.html content="Our API is backward-compatible. For more details see [Versioning and Backward Compatibility](prod_versioning.html)." %}

## Endpoints

All services may be accessed via the following URLs:

|SANDBOX|https://sandbox.nuapay.com/tpp/|
|PRODUCTION| https://api.nuapay.com/tpp/|

To request an API Key please contact our Support Team: <a href="mailto:api.support@nuapay.com">api.support@nuapay.com</a>.


{% include links.html %}
