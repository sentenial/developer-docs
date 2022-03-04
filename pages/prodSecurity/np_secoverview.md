---
title: Security Overview
keywords: Security Overview
summary: "Because you are working with sensitive financial data, we ensure that our Nuapay API is highly secure."
sidebar: sec_sidebar
permalink: np_secoverview.html
folder: prodSecurity
toc: false
---

To ensure that your data is always protected, all requests are:

* Transmitted via Secure Sockets Layer (SSL) over the HTTPS protocol.
* Pass a specific API Key unique to each merchant, for authentication or an OAuth token.
* Originate from an allowed IP address (the allowed IP addresses will be configured for you when you register for the service)

In addition to this, as an extra security layer:

* For certain endpoints (e.g. Credit-Transfer-related requests), you must provide a JOSE Header in your requests.
* To do this you will need to create a private key and certificate and use these to generate the JOSE Header. See <a href="np_secjws.html">JSON Web Signature</a> for more on this. 

{% include links.html %}
