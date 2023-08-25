---
title: Quick Start AIS Initiation
keywords: Open Banking Quick Start
summary: "Quick Start - Let's make an Account Access request!"
sidebar: ob_sidebar
permalink: ob_aisquickstart.html
folder: prodOpenBanking
---

## Overview

This section gives an overview of the API calls required when integrating via the following models:

* SELF-HOSTED
* SELF-HOSTED-CALLBACK

See [AIS Implementation Options](ob_aisimplementations.html) for more on these options.

Depending on the setup that best suits your business needs, the API calls that you need to make and how you process the responses vary.


## A Note on Authentication

When interacting with the Nuapay Endpoints you must be authenticated via one of the following:

* API Keys
* OAuth Tokens

For more details, and to decide on the approach that suits your business needs, see the available [Authentication Options](np_secapikeyauth.html) under the Security section.

## Self-Hosted

Call the following services in this order:

|[<span class="label label-info">POST</span>](tok_reqtokorg.html)| [Access Token](tok_reqtokorg.html)| (Optional) Use this service to retrieve an OAuth token, which you will use to authenticate yourself in subsequent calls. Alternatively you may use your API Key.|
|[<span class="label label-success">GET</span>](ob_getbank.html#retrieve-banks-endpoint)| [Retrieve Banks](ob_getbank.html#retrieve-banks-endpoint)| Use this service to give your <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> a list of banks from which to choose. In your request, filter on `services` = `AISP`|
|-|-|The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank (also referred to as the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>). |
|[<span class="label label-info">POST</span>](ob_createconsent.html))|[Create Consent](ob_createconsent.html)| Once the user selects an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>, pass its `bankId` in the consent request.|
|-|-|The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> is redirected to authenticate and approve the access request on that ASPSP's online banking portal. Once the user approves or declines the request, he/she is redirected to the `merchantPostAuthUrl` (as referenced in the Create Consent call). |
|[<span class="label label-success">GET</span>](ob_retrieveconsent.html)|[Retrieve Consent](ob_retrieveconsent.html)| Retrieve the status of the consent request.|

For more details on this see the [Merchant-Level Self-Hosted Setup](ob_selfsetupoverviewmerch.html)

## Self-Hosted Callback

Call the following services in this order:

|[<span class="label label-info">POST</span>](tok_reqtokorg.html)| [Access Token](tok_reqtokorg.html)| Use this service to retrieve an OAuth token, which you will use to authenticate yourself in subsequent calls.|
|[<span class="label label-success">GET</span>](ob_getbank.html#retrieve-banks-endpoint)| [Retrieve Banks](ob_getbank.html#retrieve-banks-endpoint)| Use this service to give your <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> a list of banks from which to choose. In your request, filter on `services` = `AISP`|
|-|-|The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank (also referred to as the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>). |
|[<span class="label label-info">POST</span>](ob_createpayment.html#create-payment-endpoint)|[Create Consent](ob_createconsent.html)| Once the user selects an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>, pass its `bankId` in the consent request.|
|-|-|The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> is redirected to authenticate and approve the consent on that ASPSP's online banking portal. Once the user approves or declines the request he/she is redirected to the `merchantPostAuthUrl` (as referenced in the Create Consent call). |
|[<span class="label label-info">POST</span>](tok_reqtokorg.html)| [Access Token](tok_reqtokorg.html)| Pass your merchant API Key with the required scope = `openbanking_callback` to retrieve an OAuth access token.|
|[<span class="label label-info">POST</span>](ob_forwardaccessconsent.html)|[Forward Account Access Consent Callback](ob_forwardaccessconsent.html)| In this mode as the callback/redirect from the ASPSP does not go directly to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a>, it is required to forward the details via this service; you must pass your `callbackAccessToken` and the `callbackParams`|
|[<span class="label label-success">GET</span>](ob_retrieveconsent.html)|[Retrieve Consent Status](ob_retrieveconsent.html)| Retrieve the status of the consent.|

Once you have an `ACTIVE` consent you may use the [List Accounts](ob_listaccount.html) service to retrieve account details.
