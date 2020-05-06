---
title: PISP Implementation Options
keywords: Open Banking PISP Implementation Options
summary: "Payment Initiation Service Provider Checkout Page implementation Options"
sidebar: ob_sidebar
permalink: ob_pispimplementation.html
folder: prodOpenBanking
---

Your PISP checkout page may be implemented in one of the following ways:

1. CHECKOUT
1. SELF_HOSTED
1. SELF_HOSTED_CALLBACK


|**Checkout**|This mode lets you use the Nuapay user interface for Bank Selection.|
|**Self-Hosted**| The user interface is handled by you, the merchant (or partner, acting on behalf of a merchant) for PSU Bank Selection; callback handling is through the Nuapay TPP.|
|**Self-Hosted-Callback**| In this mode the user interface is handled by you, the merchant (or partner, acting on behalf of a merchant) and you manage the PSU's experience after interacting with an ASPSP: the Callback bypasses the Nuapay TPP, you manage the callback URL that is required for each ASPSP interaction|

{% include warning.html content="SELF_HOSTED_CALLBACK mode is currently only available in the Nuapay Test environment." %}


## What is the Best Approach? 

Each approach has its advantages and disadvantages - the table below summarises the different implementations  

|**Mode**|**Advantages**|**Disadvantages**|
|Checkout| Easier implementation; No bespoke UI design (e.g. for the Bank Selection screen) is required; No TPP license is required.|No UI customisation is possible; "Powered by Nuapay" is displayed on the UI.|
|Self-Hosted| Full control over the user interface | Requires more development effort; Requires a call to the List Bank service; following the PSU's interaction on the selected ASPSP, the Callback URL redirects the user to the Nuapay TPP.| 
|Self-Hosted-Callback|Full control over the user interface and the Callback URL; it is possible to bypass the Nuapay TPP application|Requires additional development effort; Requires a call to the List Bank service; Registration of the callback URL (via Software Statement Assertions in the UK Open Banking scheme, for example) at each ASPSP is required.|


## Checkout Mode 

In **Checkout** mode (for Partners) you will: 

1. Use your partner-level API key to retrieve the [list of your merchants](ob_partnerintegration.html#api-details---get-organisations) and [retrieve a token](ob_partnerintegration.html#api-details---post-tokens) representing the required merchant.
1. Call the `/payments` endpoint on behalf of your merchant, using the OAuth token retrieved in the previous step (see [Create Payment](ob_createpayment.html)) and set the `integrationType` to `CHECKOUT`. Manage the returned payment identifier with some Nuapay-provided JS and CSS to render the Bank Selection screen for your payers. 
1. PSU selects a bank.
1. Redirect the PSU to the ASPSP to authorise the payment.
1. Process the callback URL; display the status to the PSU and close the TPP UI, passing control to the parent window.
1. Use [Retrieve Payment](ob_retrievepayment.html) to determine the final payment status, if required (an optional step). 

A detailed overview of the various steps involved in this flow is provided in the image below.

{% include tip.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}

{% include image.html file="ob_checkout_flow.png" url="images/ob_checkout_flow-partner.png" target = "_new" alt="Checkout Flow - Partner" caption="CHECKOUT Flow - Partner" %}

For more on this see [Checkout Payment Page Setup](ob_setupoverview.html).


## Self-Hosted Mode 

In **Self-Hosted** mode (for Partners):

1. Use your partner-level API key to retrieve the [list of your merchants](ob_partnerintegration.html#api-details---get-organisations) and [retrieve a token](ob_partnerintegration.html#api-details---post-tokens) representing the required merchant.
1. You will design your own Bank Selection screen; use [Retrieve Banks](ob_getbank.html) to populate your interface. 
1. Once the payer has selected a bank, call the `/payments` endpoint using the OAUth token, representing the required merchant, (see [Create Payment](ob_createpayment.html)).
Set the `integrationType` to `SELF_HOSTED`, specify the `bankId` provided by the payer and set the `merchantPostAuthUrl`.
1. Redirect the PSU to the ASPSP to authorise the payment. The `callbackUrl` is hard-coded for the Nuapay TPP.
1. Process the callback URL to the configured merchantPostAuthUrl.
1. Use [Retrieve Payment](ob_retrievepayment.html) to determine the final payment status, if required (an optional step). 

A detailed overview of the various steps involved in this flow is provided in the image below.

{% include tip.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}

{% include image.html file="ob_selfhosted_flow-partner.png" url="images/ob_selfhosted_flow-partner.png" target = "_new" alt="Self-Hosted Flow" caption="SELF_HOSTED Partner Flow" %}


For more on this see [Self-Hosted Payment Page Setup](ob_selfsetupoverview.html)


## Self-Hosted-Callback Mode 

{% include warning.html content="SELF_HOSTED_CALLBACK mode is currently only available in the Nuapay Test environment." %}

{% include note.html content="If you want to use this mode you must have first registered your OAuth 2.0 Callback Handler with the platform. Your Account Manager can provide you with more information on this." %}

In **Self-Hosted-Callback** mode:

1. Using your partner-level API key retrieve the [list of your merchants](ob_partnerintegration.html#api-details---get-organisations) and [retrieve a token](ob_partnerintegration.html#api-details---post-tokens) representing the required merchant.
1. You will design your own Bank Selection screen; use [Retrieve Banks](ob_getbank.html) to populate your interface. 
1. Once the payer has selected a bank, call the `/payments` endpoint using the OAUth token, representing the required merchant, (see [Create Payment](ob_createpayment.html)).
Set the `integrationType` to `SELF_HOSTED_CALLBACK`, specify the `bankId` provided by the payer and set the `merchantPostAuthUrl`.
1. Redirect the PSU to the ASPSP to authorise the payment - note that in this mode the `callbackUrl` = the `merchantPostAuthUrl`.
   * Unlike in the SELF_HOSTED mode, the OAuth callback from the bank is not passed to the Nuapay TPP directly, instead it is directed to the merchantPostAuthUrl. 
   * The partner retrieves An OAuth token.
   * The payment callback is passed to the Nuapay TPP.
1. Process the callback and confirm the payment status.
1. Use [Retrieve Payment](ob_retrievepayment.html) to determine the final payment status, if required (an optional step). 

A detailed overview of the various steps involved in this flow is provided in the image below.

{% include tip.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}
{% include image.html file="ob_selfhostedcallback_flow-partner.png" url="images/ob_selfhostedcallback_flow-partner.png" target = "_new" alt="Self-Hosted-Callback Partner Flow" caption="SELF_HOSTED_CALLBACK Partner Flow" %}

