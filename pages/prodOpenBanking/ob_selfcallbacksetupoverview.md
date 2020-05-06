---
title: Self-Hosted-Callback Payment Page Setup
keywords: Self Hosted Callback Payment Page Setup Javascript Add Open Banking Payment Page
summary: "Adding Open Banking (in Self-Hosted-Callback mode) lets you fully control your PSU's payment journey and allows you to bypass the Nuapay TPP."
sidebar: ob_sidebar
permalink: ob_selfcallbacksetupoverview.html
folder: prodOpenBanking
toc: false
---

## Overview

{% include warning.html content="SELF_HOSTED_CALLBACK mode is currently only available in the Nuapay Test environment." %}


{% include note.html content="This section is for users who want to use the **SELF_HOSTED_CALLBACK** mode - see [Implementation Options](ob_pispimplementation.html) for more on this." %}

## Prerequisites

In this mode, once a PSU has been redirected to a selected ASPSP and has completed his/her interactions with that bank, you specify the callback/redirect URL (the `merchantPostAuthUrl`) to where that payer is then redirected. 

In order for this to happen an ASPSP must do two things:

1. Determine what the callback URL is for the specific PSU.
1. Confirm that this URL has been properly configured and registered (with that ASPSP).

To configure a callback URL with an ASPSP:

1. You must have a TPP license. 
1. Register the callback URL in your ASPSP application (this is the Software Statement Assertion (SSA) in the UK Open Banking scheme).
1. If you have already registered an SSA for UK Open Banking but had not specified any callback URLs, you will need to generate a new Software Statement in the Open Banking Directory and set the new callback URLs there. You may specify multiple callback URLs; as a partner you may want to specify different callback URLs for each of your merchants, for example.

Note that:

* A Callback URL is a url that has been listed as one of the redirect urls defined in the Software Statement in the Open Banking directory.
* ASPSPs will not process psuAuthUrls containing callbacks that are different to the ones used when the TPP registered with them.


{% include important.html content="The Nuapay API Support team manage the TPP-to-ASPSP registration process including SSA management and callback URL registration. Please contact your Account Manager if you need to register a new callback URL." %}

## Sequence Steps

To use Self-Hosted-Callback mode (as a partner):

1. Use your partner-level API key to retrieve the [list of your merchants](ob_partnerintegration.html#api-details---get-organisations) and [retrieve a token](ob_partnerintegration.html#api-details---post-tokens) representing the required merchant.
1. You will design your own Bank Selection screen; use [Retrieve Banks](ob_getbank.html) to populate your interface. 
1. Once the payer has selected a bank, call the `/payments` endpoint using the OAUth token, representing the required merchant, (see [Create Payment](ob_createpayment.html)).
Set the `integrationType` to `SELF_HOSTED_CALLBACK`, specify the `bankId` provided by the payer and set the `merchantPostAuthUrl`.
1. Redirect the PSU to the ASPSP to authorise the payment - note that in this mode the `callbackUrl` = the `merchantPostAuthUrl`.
   * Unlike in the SELF_HOSTED mode, the redirect is not passed to the Nuapay TPP directly, instead it is directed to the merchantPostAuthUrl. 
   * The partner retrieves An OAuth token.
   * The payment callback is passed to the Nuapay TPP.
1. Process the callback and confirm the payment status.
1. Use [Retrieve Payment](ob_retrievepayment.html) to determine the final payment status, if required (an optional step). 


|For a merchant integration the flow is similar but rather than having to retrieve a list of merchants and retrieve an access token, a merchant-level API key (or OAUth token) is required when calling the Nuapay services.|


## Handling the Callback

The key stage in the Self-Hosted-Callback implementation is handling the ASPSP redirect. See Step 4.1 in the flow below:

{% include image.html file="ob_selfhostedcallback_flow-partner.png" url="images/ob_selfhostedcallback_flow-partner.png" target = "_new" alt="Self-Hosted-Callback Partner Flow" caption="SELF_HOSTED_CALLBACK Partner Flow" %}

In this step you need to forward the callback to the Nuapay TPP:

1. Parse the callback URL parameters.
1. Send a request to the Nuapay OAuth Server.
1. The OAuth Server authenticates you (as merchant or partner) and passes back a token.
1. Use this token to [Forward the payment callback](ob_forward_callback.html) to the Nuapay TPP.








{% include links.html %}






