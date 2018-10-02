---
title: Security Overview
keywords: Security Overview
summary: "Because you are working with sensitive financial data, we ensure that our Nuapay API is highly secure."
sidebar: np_sidebar
permalink: np_secoverview.html
folder: prodNuapay
toc: false
---


We use API Keys to ensure the security of your sensitive data, which is transmitted via Secure Sockets Layer (SSL) over the HTTPS protocol.

For certain endpoints you must provide a JOSE Header in your requests. To do this you will need to create a private key and certificate and use these to generate the JOSE Header. See <a href="np_secjws.html">JSON Web Signature</a> for more on this. 


{% include links.html %}
