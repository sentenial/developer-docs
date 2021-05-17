---
title: Partner Quick Start PISP Initiation
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
* REDIRECT

See [PISP Implementation Options](ob_pispimplementations.html) for more on these options.

Depending on the setup that best suits your business needs, the API calls that you need to make and how you process the responses vary. 

## Postman Collection

|<img src="images/postman-logo.png">|<br>We highly recommend that you use **Postman** to test our PISP APIs on the Sandbox environment. Download it for free from <a href= "https://www.postman.com/downloads/" target="_blank">www.postman.com/downloads</a>.<br>| 


{% include tip.html content="Unlike the Swagger specification, the Postman Collection we've created allows you to work with the APIs directly in our Sandbox environment. While our Swagger file is a formal definition of our PISP service, which you can use to generate client libraries, the Postman Collection logically groups the services together so that you can see the business logic of why (and when) to call the various PISP endpoints."%} 

You will need to download:

* A Collection `.JSON` file. 
* An Environment `.JSON` file.

{% include callout.html content="Download the files from Github here: <a href= 'https://github.com/sentenial/postman-collections/tree/master/collections/open_banking/open_banking_partners' target='_blank'><span class='label label-success'>Postman Collections on Github</span></a> <br/><br/> If you are new to Postman and are unsure how to import the collection, please see the <a href ='https://github.com/sentenial/postman-collections/blob/master/README.md#what-are-postman-collections' target='_blank'>README</a>." type="primary" %} 

Once you have donwloaded the *Collection* and the *Environment* files:

1. Open Postman.
1. Import the collection files.
1. Specify your API Key.

{% include tip.html content="If you don't already have one, contact our Support Team to request an API Key: <a href='mailto:api.support@nuapay.com'>api.support@nuapay.com</a>."%} 


## Checkout Mode

{% include note.html content="CHECKOUT and REDIRECT is only available for merchants who want to process GBP payments; if you want to process EUR transactions then you must go with either the SELF-HOSTED or SELF-HOSTED-CALLBACK integration."%} 


As a partner, you will need to interact with the Nuapay Open Banking services on behalf of your merchants. In this example we will assume that you want to set up a payment for Merchant X but do not have the merchant identifier and need to query the `GET /organisations` service to retrieve it as a first step.

Call the following services in this order

|[<span class="label label-success">GET</span>](ob_partnerintegration.html#api-details---get-organisations)| [Organisations](ob_partnerintegration.html#api-details---get-organisations)| (Optional) Use this service to retrieve the list of organisations/merchants under you as the Partner entity. Use your Partner-level API Key and store the required merchant identifier.|
|[<span class="label label-info">POST</span>](ob_partnerintegration.html#api-details---post-tokens)| [Access Token](ob_partnerintegration.html#api-details---post-tokens)| Use this service to retrieve an OAuth token for the required merchant. Pass your API Key and merchantId with scope = `openbanking_pisp`.|
|[<span class="label label-info">POST</span>](ob_createpayment.html#create-payment-endpoint)|[Create Payment](ob_createpayment.html#create-payment-endpoint)| Call this service with the merchant access token; the Create Payment service generates an Open Banking payment object, returning a unique `userInterfacePaymentId` with an (initial) [status](ob_paymentstatuses.html) of `PENDING`. Apply the Nuapay-provided JS and CSS on your page to render the Bank Selection screen for your merchant's payers.|
|-|-|The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank (also referred to as the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>) and is redirected to authenticate and approve the payment on that ASPSP's online banking portal.|
|[<span class="label label-success">GET</span>](ob_retrievepayment.html#retrieve-payment-endpoint)|[Retrieve Payment Status](ob_retrievepayment.html#retrieve-payment-endpoint)| Retrieve the status of the payment.|

For more details on this see the [Partner-level Checkout Setup](ob_checkoutoverview.html). 

## Self-Hosted

As a partner, you will need to interact with the Nuapay Open Banking services on behalf of your merchants. In this example we will assume that you want to set up a payment for Merchant X but do not have the merchant identifier and need to query the `GET /organisations` service to retrieve it as a first step.

Call the following services in this order:

|[<span class="label label-success">GET</span>](ob_partnerintegration.html#api-details---get-organisations)| [Organisations](ob_partnerintegration.html#api-details---get-organisations)| (Optional) Use this service to retrieve the list or organisations/merchants under you as the Partner entity. Use your Partner-level API Key and store the required merchant identifier.|
|[<span class="label label-info">POST</span>](ob_partnerintegration.html#api-details---post-tokens)| [Access Token](ob_partnerintegration.html#api-details---post-tokens)| Use this service to retrieve an OAuth token for the required merchant. Pass your API Key and merchantId with scope = `openbanking_pisp`.|
|[<span class="label label-success">GET</span>](ob_getbank.html#retrieve-banks-endpoint)| [Retrieve Banks](ob_getbank.html#retrieve-banks-endpoint)| Use this service to give your <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> a list of banks from which to choose|
|-|-|The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank (also referred to as the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>). |
|[<span class="label label-info">POST</span>](ob_createpayment.html#create-payment-endpoint)|[Create Payment](ob_createpayment.html#create-payment-endpoint)| Once the user selects an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>, pass its `bankId` in the payment request.|
|-|-|The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> is redirected to authenticate and approve the payment on that ASPSP's online banking portal. Once the user approves or declines the payment he/she is redirected to the `merchantPostAuthUrl` (as referenced in the Create Payment call). |
|[<span class="label label-success">GET</span>](ob_retrievepayment.html#retrieve-payment-endpoint)|[Retrieve Payment Status](ob_retrievepayment.html#retrieve-payment-endpoint)| Retrieve the status of the payment.|



For more details on this see the [Partner-Level Self-Hosted Setup](ob_selfsetupoverview.html)

## Self-Hosted Callback

As a partner, you will need to interact with the Nuapay Open Banking services on behalf of your merchants. In this example we will assume that you want to set up a payment for Merchant X but do not have the merchant identifier and need to query the service to retrieve it.

Call the following services in this order:

|[<span class="label label-success">GET</span>](ob_partnerintegration.html#api-details---get-organisations)| [Organisations](ob_partnerintegration.html#api-details---get-organisations)| (Optional) Use this service to retrieve the list or organisations/merchants under you as the Partner entity. Use your Partner-level API Key and store the required merchant identifier.|
|[<span class="label label-info">POST</span>](ob_partnerintegration.html#api-details---post-tokens)| [Access Token](ob_partnerintegration.html#api-details---post-tokens)| Use this service to retrieve an OAuth token for the required merchant. Pass your API Key and merchantId with scope = `openbanking_pisp`.|
|[<span class="label label-success">GET</span>](ob_getbank.html#retrieve-banks-endpoint)| [Retrieve Banks](ob_getbank.html#retrieve-banks-endpoint)| Use this service to give your <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> a list of banks from which to choose|
|-|-|The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank (also referred to as the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>). |
|[<span class="label label-info">POST</span>](ob_createpayment.html#create-payment-endpoint)|[Create Payment](ob_createpayment.html#create-payment-endpoint)| Once the user selects an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>, pass its `bankId` in the payment request.|
|-|-|The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> is redirected to authenticate and approve the payment on that ASPSP's online banking portal. Once the user approves or declines the payment he/she is redirected to the `merchantPostAuthUrl` (as referenced in the Create Payment call). |
|[<span class="label label-info">POST</span>](ob_tokenmgmt.html#request-an-access-token)| [Access Token](ob_tokenmgmt.html#request-an-access-token)| Pass your Partner API Key with the required scope = `openbanking_callback` to retrieve an OAuth access token.|
|[<span class="label label-info">POST</span>](ob_paymentcallback.html#forward-payment-callback-endpoint)|[Forward Payment Callback](ob_paymentcallback.html#forward-payment-callback-endpoint)| In this mode as the callback/redirect from the ASPSP does not go directly to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a>, it is required to forward the details via this service; you must pass your `callbackAccessToken` and the `callbackParams`|
|[<span class="label label-success">GET</span>](ob_retrievepayment.html#retrieve-payment-endpoint)|[Retrieve Payment Status](ob_retrievepayment.html#retrieve-payment-endpoint)| Retrieve the status of the payment.|

For more details, see [Partner Self-Hosted-Callback Payment Page Setup](ob_selfcallbacksetupoverview.html).

## Redirect Mode

{% include note.html content="CHECKOUT and REDIRECT is only available for merchants who want to process GBP payments; if you want to process EUR transactions then you must go with either the SELF-HOSTED or SELF-HOSTED-CALLBACK integration."%} 

As a partner, you will need to interact with the Nuapay Open Banking services on behalf of your merchants. In this example we will assume that you want to set up a payment for Merchant X but do not have the merchant identifier and need to query the `GET /organisations` service to retrieve it as a first step.

Call the following services in this order

|[<span class="label label-success">GET</span>](ob_partnerintegration.html#api-details---get-organisations)| [Organisations](ob_partnerintegration.html#api-details---get-organisations)| (Optional) Use this service to retrieve the list of organisations/merchants under you as the Partner entity. Use your Partner-level API Key and store the required merchant identifier.|
|[<span class="label label-info">POST</span>](ob_partnerintegration.html#api-details---post-tokens)| [Access Token](ob_partnerintegration.html#api-details---post-tokens)| Use this service to retrieve an OAuth token for the required merchant. Pass your API Key and merchantId with scope = `openbanking_pisp`.|
|[<span class="label label-info">POST</span>](ob_createpayment.html#create-payment-endpoint)|[Create Payment](ob_createpayment.html#create-payment-endpoint)| Call this service with the merchant access token. The `integrationType` must be set to REDIRECT and the `merchantPostAuthUrl` must be provided. The Create Payment service generates an Open Banking payment object, returning a unique `userInterfacePaymentId` with the payment object having an (initial) [status](ob_paymentstatuses.html) of `PENDING`. The URI must be passed to the PSU; once the user click the link the Bank Selection screen is launched in a new browser window/tab.|
|-|-|The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank and is redirected to authenticate and approve the payment on that ASPSP's online banking portal.|
|[<span class="label label-success">GET</span>](ob_retrievepayment.html#retrieve-payment-endpoint)|[Retrieve Payment Status](ob_retrievepayment.html#retrieve-payment-endpoint)| Retrieve the status of the payment.|

For more details on this see the [Partner-level Redirect Setup](ob_redirectoverview.html). 











