---
title: PISP Implementation Options
keywords: Open Banking PISP Implementation Options
summary: "Payment Initiation Service Provider Checkout Page implementation Options"
sidebar: ob_sidebar
permalink: ob_pispimplementation.html
folder: prodOpenBanking
---

Your PISP checkout page may be implemented in one of two ways:

1. CHECKOUT
1. SELF_HOSTED


|**Checkout**|In this mode you can leverage on the Nuapay user interface for the Bank selection, bank confirmation and payment submission confirmation screens.|
|**Self-Hosted**| The user interface is handled by you, the merchant (or partner, acting on behalf of a merchant).|

## Checkout Mode

In **Checkout** mode you will: 

1. Retrieve the appropriate authorisation (API Key or OAuth token).
1. Call the `/payments` endpoint (see [Create Payment](ob_createpayment.html)) and set the `integrationType` to `CHECKOUT`
1. Manage the returned payment identifier with some Nuapay-provided JS and CSS to render the Bank Selection screen for your payers. 

A detailed overview of the various steps involved in this flow is provided in the image below.

{% include note.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}

{% include image.html file="ob_checkout_flow.png" url="images/ob_checkout_flow.png" target = "_new" alt="Checkout Flow" caption="CHECKOUT Flow" %}

For more on this see [Checkout Payment Page Setup](ob_setupoverview.html).


## Self-Hosted Mode

In **Self-Hosted** mode:

1. You will design your own Bank Selection screen; use [Retrieve Banks](ob_getbank.html) to populate your interface. 
1. Once your payer has selected a bank, call the `/payments` endpoint (see [Create Payment](ob_createpayment.html))
1. Set the `integrationType` to `SELF_HOSTED`
1. Specify the `bankId` provided by the payer in step 2
1. Manage the returned payment identifier as required.

A detailed overview of the various steps involved in this flow is provided in the image below.

{% include note.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}

{% include image.html file="ob_selfhosted_flow.png" url="images/ob_selfhosted_flow.png" target = "_new" alt="Self-Hosted Flow" caption="SELF_HOSTED Flow" %}


For more on this see [Self-Hosted Payment Page Setup](ob_selfsetupoverview.html)



