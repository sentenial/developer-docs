---
title: Self-Hosted Payment Page Setup
keywords: Self Hosted Payment Page Setup Javascript Add Open Banking Payment Page
summary: "Adding Open Banking (Self-Hosted mode) as a payment option to your Payment Page requires configuration as outlined below. In Self-Hosted mode you must develop your own user interface."
sidebar: ob_sidebar
permalink: ob_selfsetupoverviewmerch.html
folder: prodOpenBanking
toc: false
---

{% include note.html content="This section is for **Merchant** users who want to use the **SELF_HOSTED** mode - see [Implementation Options](ob_pispimplementation.html) for more on this." %}

## Overview 

To add Open Banking to your payment page you will need to carry out the following steps:

1. Use your API key to retrieve a merchant access token. (For more on this see [retrieving tokens](ob_partnerintegration.html#api-details---post-tokens)).
1. Call GET `/banks` to retrieve a list of all supported banks (see [Retrieve Banks](ob_getbank.html)) to populate your Bank Selection screen. 
1. Once the payer has selected a bank, call the `/payments` endpoint using the OAUth token, (see [Create Payment](ob_createpayment.html)).
Set the `integrationType` to `SELF_HOSTED`, specify the `bankId` provided by the payer and set the `merchantPostAuthUrl` (this can be the partner or merchant URL). This will return the `aspspAuthUrl`, to which you can redirect your <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a>.
1. Your payer interacts with the selected <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> to authorise the payment. 
1. The TPP posts the payment ID to the partner/merchant URL (`merchantPostAuthUrl`).
1. Use [Retrieve Payment](ob_retrievepayment.html) to determine the final payment status, if required (an optional step) or, alternatively, use Webhooks. 

A detailed overview of the various steps involved in this flow is provided in the image below.

{% include tip.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}

{% include image.html file="ob_selfhosted_flow-merchant.png" url="images/ob_selfhosted_flow-merchant.png" target = "_new" alt="Self-Hosted Flow" caption="SELF_HOSTED Merchant Flow" %}


{% include links.html %}






