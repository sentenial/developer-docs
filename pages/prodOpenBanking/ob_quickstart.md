---
title: Quick Start
keywords: Open Banking Quick Start
summary: "Quick Start - Let's make an Open Banking payment!"
sidebar: ob_sidebar
permalink: ob_quickstart.html
folder: prodOpenBanking
---

## Merchant Integrations

|SELF-HOSTED MODE|

Call the following services in this order:

|<span class="label label-success">GET</span>| [Retrieve Banks](ob_getbank.html)| Use this service to give your PSU a list of banks from which to choose|
|<span class="label label-info">POST</span>|[Create Payment](ob_createpayment.html)| Once the user select a bank, pass the payment request to the ASPSP.|
|<span class="label label-success">GET</span>|[Retrieve Payment Status](ob_retrievepayment.html)| Retrieve the status of the payment|

|CHECKOUT MODE|

Call the following services in this order:


|SELF-HOSTED-CALLBACK Mode|

Call the following services in this order:

## Partner Integrations

**SELF-HOSTED MODE**

|For a [Partner Integration](ob_integrationoverview.html#partner-integration) in [Self-Hosted](ob_pispimplementation.html#self-hosted-mode) mode|

Call the following services in this order:

|<span class="label label-success">GET</span>| [List Partner's Merchants](ob_partnerintegration.html#api-details---get-organisations)| Use `GET /organisations` service to retrieve all merchants linked to you as a partner entity.|
|<span class="label label-success">GET</span>| [Retrieve Banks](ob_getbank.html)| Use this service to give your selected merchant's PSU a list of banks from which to choose|
|<span class="label label-info">POST</span>| [Request Access Token for Merchant](ob_getbank.html)| Use this service to give your PSU a list of banks from which to choose|
|<span class="label label-info">POST</span>|[Create Payment (on behalf of merchant)](ob_createpayment.html)| Use the OAuth token representing the selected merchant to create the payment|
|<span class="label label-success">GET</span>|[Retrieve Payment Status](ob_retrievepayment.html)| Retrieve the status of the payment|











