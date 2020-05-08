---
title: Quick Start Payment Initiation for Partners
keywords: Open Banking Quick Start
summary: "Quick Start - Let's make an Open Banking payment!"
sidebar: ob_sidebar
permalink: ob_quickstartpart.html
folder: prodOpenBanking
---

## Overview

This section gives **partners** an overview of the API calls required for the three integration models:

* CHECKOUT
* SELF-HOSTED
* SELF-HOSTED-CALLBACK

See [PISP Implementation Options](ob_pispimplementations.html) for more on these options.

Depending on the setup that best suits your business needs, the API calls that you need to make and how you process the responses vary. 

The following sections give a high-level summary of the calls required for each of the integration models.

## Checkout Mode

As a partner, you will need to interact with the Nuapay Open Banking services on behalf of your merchants. In this example we will assume that you want to set up a payment for Merchant X but do not have the merchant identifier and need to query the `GET /organisations` service to retrieve it as a first step.

Call the following services in this order

|[<span class="label label-success">GET</span>](ob_partnerintegration.html#api-details---get-organisations)| [Organisations](ob_partnerintegration.html#api-details---get-organisations)| (Optional) Use this service to retrieve the list or organisations/merchants under you as the Partner entity. Use your Partner-level API Key and store the required merchant identifier.|
|[<span class="label label-info">POST</span>](ob_partnerintegration.html#api-details---post-tokens)| [Access Token](ob_partnerintegration.html#api-details---post-tokens)| Use this service to retrieve an OAuth token for the required merchant. Pass your API Key and merchantId with scope = `openbanking_pisp`.|
|[<span class="label label-info">POST</span>](ob_createpayment.html#create-payment-endpoint)|[Create Payment](ob_createpayment.html#create-payment-endpoint)| Call this service with the merchant access token; the Create Payment service generates an Open Banking payment object, returning a unique `paymentId` with an (initial) status of PENDING_APPROVAL. Manage the returned payment identifier with some Nuapay-provided JS and CSS to render the Bank Selection screen for your merchant's payers.|
|-|-|The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank (also referred to as the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>) and is redirected to authenticate and approve the payment on that ASPSP's online banking portal.|
|[<span class="label label-success">GET</span>](ob_retrievepayment.html#retrieve-payment-endpoint)|[Retrieve Payment Status](ob_retrievepayment.html#retrieve-payment-endpoint)| Retrieve the status of the payment.|

For more details on this see the [Partner-level Checkout Setup](ob_checkoutoverview.html). 

## Self-Hosted

As a partner, you will need to interact with the Nuapay Open Banking services on behalf of your merchants. In this example we will assume that you want to set up a payment for Merchant X but do not have the merchant identifier and need to query the `GET /organisations` service to retrieve it as a first step.

Call the following services in this order:

|[<span class="label label-success">GET</span>](ob_partnerintegration.html#api-details---get-organisations)| [Organisations](ob_partnerintegration.html#api-details---get-organisations)| (Optional) Use this service to retrieve the list or organisations/merchants under you as the Partner entity. Use your Partner-level API Key and store the required merchant identifier.|
|[<span class="label label-info">POST</span>](ob_partnerintegration.html#api-details---post-tokens)| [Access Token](ob_partnerintegration.html#api-details---post-tokens)| Use this service to retrieve an OAuth token for the required merchant. Pass your API Key and merchantId with scope = `openbanking_pisp`.|
|[<span class="label label-success">GET</span>](ob_getbank.html#retrieve-banks-endpoint)| [Retrieve Banks](ob_getbank.html#retrieve-banks-endpoint)| Use this service to give your <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> a list of banks from which to choose|
|[<span class="label label-info">POST</span>](ob_createpayment.html#create-payment-endpoint)|[Create Payment](ob_createpayment.html#create-payment-endpoint)| Once the user select a bank, pass the payment request to the ASPSP.|
|-|-|The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank (also referred to as the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>) and is redirected to authenticate and approve the payment on that ASPSP's online banking portal.|
|[<span class="label label-success">GET</span>](ob_retrievepayment.html#retrieve-payment-endpoint)|[Retrieve Payment Status](ob_retrievepayment.html#retrieve-payment-endpoint)| Retrieve the status of the payment.|


For more details on this see the [Partner-Level Self-Hosted Setup](ob_selfsetupoverview.html)

## Self-Hosted Callback

As a partner, you will need to interact with the Nuapay Open Banking services on behalf of your merchants. In this example we will assume that you want to set up a payment for Merchant X but do not have the merchant identifier and need to query the service to retrieve it.

Call the following services in this order:

|[<span class="label label-success">GET</span>](ob_partnerintegration.html#api-details---get-organisations)| [Organisations](ob_partnerintegration.html#api-details---get-organisations)| (Optional) Use this service to retrieve the list or organisations/merchants under you as the Partner entity. Use your Partner-level API Key and store the required merchant identifier.|
|[<span class="label label-info">POST</span>](ob_partnerintegration.html#api-details---post-tokens)| [Access Token](ob_partnerintegration.html#api-details---post-tokens)| Use this service to retrieve an OAuth token for the required merchant. Pass your API Key and merchantId with scope = `openbanking_pisp`.|
|[<span class="label label-success">GET</span>](ob_getbank.html#retrieve-banks-endpoint)| [Retrieve Banks](ob_getbank.html#retrieve-banks-endpoint)| Use this service to give your <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> a list of banks from which to choose|
|[<span class="label label-info">POST</span>](ob_createpayment.html#create-payment-endpoint)|[Create Payment](ob_createpayment.html#create-payment-endpoint)| Once the user select a bank, pass the payment request to the ASPSP.|
|-|-|The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank (also referred to as the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>) and is redirected to authenticate and approve the payment on that ASPSP's online banking portal.|
|[<span class="label label-info">POST</span>](ob_partnerintegration.html#api-details---post-tokens)|[Access Token](ob_partnerintegration.html#api-details---post-tokens)| Pass your merchantAPIKey with scope = `openbanking_callback`|
|[<span class="label label-info">POST</span>](ob_paymentcallback.html#forward-payment-callback-endpoint)|[Forward Payment Callback](ob_paymentcallback.html#forward-payment-callback-endpoint)| In this mode as the callback/redirect from the ASPSP does not go directly to the Nuapay TPP, it is required to forward the details via this service; you must pass your `callbackAccessToken` and the `callbackParams`|
|[<span class="label label-success">GET</span>](ob_retrievepayment.html#retrieve-payment-endpoint)|[Retrieve Payment Status](ob_retrievepayment.html#retrieve-payment-endpoint)| Retrieve the status of the payment.|

For more details, see [Partner Self-Hosted-Callback Payment Page Setup](ob_selfcallbacksetupoverview.html).











