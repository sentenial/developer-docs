---
title: Partner PISP Checkout Payment Page Setup
keywords: Checkout Payment Page Setup Javascript Add Open Banking Payment Page
summary: "Adding Open Banking (Checkout mode) as a payment option to your Payment Page requires a little configuration as outlined below. In Checkout mode you will use the Nuapay user interface for Bank Selection and Confirmation screens."
sidebar: ob_sidebar
permalink: ob_checkoutoverview.html
folder: prodOpenBanking
---

{% include note.html content="This section is for **Partner** users who want to use the **CHECKOUT** mode - see [Implementation Options](ob_pispimplementation.html) for more on this." %}

## Overview

A detailed overview of the various steps involved in the **Checkout** flow is provided in the image below.

{% include tip.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}

{% include image.html file="ob_checkout_flow.png" url="images/ob_checkout_flow-partner.png" target = "_new" alt="Checkout Flow - Partner" caption="CHECKOUT Flow - Partner" %}


In **Checkout** mode you will: 

1. Use your partner-level API key to retrieve a token representing the required merchant. (For more on this see [list organisations](ob_partnerintegration.html#api-details---get-organisations) and [retrieving tokens](ob_partnerintegration.html#api-details---post-tokens)).
1. Call the `/payments` endpoint, on behalf of the merchant, using the OAuth token retrieved in the previous step (see [Create Payment](ob_createpayment.html)) and set the `integrationType` to `CHECKOUT`. Manage the returned payment identifier with some Nuapay-provided JS and CSS to render the Bank Selection screen for your payers. 
1. The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank.
1. Redirect the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> to authorise the payment.
1. The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a> posts the payment ID to the partner/merchant URL (`merchantPostAuthUrl`).
1. Use [Retrieve Payment](ob_retrievepayment.html) to determine the final payment status, if required (an optional step). 

{% include tip.html content="Rather than redirect PSUs to the ASPSP on the desktop, you may offer a QR code on screen, which will allow users to use their mobile devices to complete the bank sign-in and payment autorisation. Because users complete the payment on a mobile devive, they can take advantage of biometric authentication, for example. For more on this see [QR Code Functionality](#qr-code-functionality) below. " %}

{% include checkout_steps.html %} <!--pulls in common steps for Partner and Merchant-->