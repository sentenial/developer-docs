---
title: General API Rules
keywords: Instant Payments API Rules
summary: "API requirements when working with Instant Payments."
sidebar: ip_sidebar
permalink: ip_apirules.html
folder: prodInstantPayments
---

Note that all requests must:

* Be sent via the HTTPS protocol.
* Pass a specific API Key, unique to each institution, for authentication.
* Originate from an allowed IP address (the allowed IP addresses will be configured for you when you register for the service).
* Include (at a minimum) the mandatory fields required for the specific request that is being made.
 
{% include note.html content="Our API is backward-compatible. For more details see [Versioning and Backward Compatibility](prod_versioning.html) under the Product Overview section." %}


{% include links.html %}
