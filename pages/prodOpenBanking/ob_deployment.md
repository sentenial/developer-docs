---
title: Open Banking Deployment
keywords: Open Banking Terminology Overview
summary: "The Open Banking TPP REST service uses HA Proxy, a HSM, Database Server and an API Gateway to connect PSUs to their ASPSPs"
sidebar: ob_sidebar
permalink: ob_deployment.html
folder: prodOpenBanking
---


Open Banking is deployed on a highly secure, monitored and hosted service. 

The service is built on:


| **HA Proxy**| The SSL Termination|
| **API Gateway**| Managing throttling, Idempotency, Load balancing and API Security|
| **TPP-REST**| The Nuapay TPP Platform|
| **HSM**| A Hardware Security Model, storing private keys, etc.|
| **Database Server**| Storing transaction details and audit trails|
| **ASPSP** | The Account Servicing Payment Service Provider (the bank in which PSUs hold an account)|

{% include image.html file="ob_deployment.png" url="images/ob_deployment.png" target = "_new" alt="Deployment Overview" caption="Deployment Overview" %}



{% include links.html %}