---
title: Self-Hosted-Callback Payment Page Setup
keywords: Self Hosted Callback Payment Page Setup Javascript Add Open Banking Payment Page
summary: "Adding Open Banking (in Self-Hosted-Callback mode) lets you fully control your PSU's payment journey and allows you to bypass the Nuapay TPP."
sidebar: ob_sidebar
permalink: ob_selfcallbackmerch.html
folder: prodOpenBanking
toc: false
---

## Overview

{% include warning.html content="SELF_HOSTED_CALLBACK mode is currently only available in the Nuapay Test environment." %}


{% include note.html content="This section is for **Merchant** users who want to use the **SELF_HOSTED_CALLBACK** mode - see [Implementation Options](ob_pispimplementation.html) for more on this." %}

## Prerequisites

In this mode, once a <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> has been redirected to a selected <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> and has completed his/her interactions with that bank, the payer is redirected to the `merchantPostAuthUrl`, as provided in the [Create Payment](ob_createpayment.html) request. 

In order for the payer to be successfully redirected, an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> must do two things:

1. Determine what the callback URL is for the specific <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a>.
1. Confirm that this URL has been properly configured and registered (with that <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>).

{% include important.html content="The Nuapay API Support team manage the TPP-to-ASPSP registration process (including callback URL registration) on behalf of our partners and merchants. Please contact your Account Manager if you need to register a new callback URL." %}


## Sequence Steps

A detailed overview of the various steps involved in the **Self-Hosted-Callback** flow is provided in the image below.

{% include tip.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}
{% include image.html file="ob_selfhostedcallback_flow-merchant.png" url="images/ob_selfhostedcallback_flow-merchant.png" target = "_new" alt="Self-Hosted-Callback Merchant Flow" caption="SELF_HOSTED_CALLBACK Merchant Flow" %}

{% include note.html content="If you want to use this mode you must have first registered your OAuth 2.0 Callback Handler with the platform. Your Account Manager can provide you with more information on this." %}

To use Self-Hosted-Callback mode:

1. Using your API key, [retrieve a token](ob_partnerintegration.html#api-details---post-tokens); set your scope = `openbanking_pisp`.
1. Call GET `/banks` to retrieve a list of all supported banks (see [Retrieve Banks](ob_getbank.html)) to populate your Bank Selection screen.  
1. Once the payer has selected a bank, call the `/tpp/payments` endpoint (see [Create Payment](ob_createpayment.html)).
Set the `integrationType` to `SELF_HOSTED_CALLBACK`, specify the `bankId` provided by the payer and set the `merchantPostAuthUrl`. The merchantPostAuthUrl will process the callback from the ASPSP, this information needs to be captured and sent to Nuapay.
1. Redirect the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> to authorise the payment - note after the PSU approves or denies the payment request they are redirected to the `merchantPostAuthUrl`.

1. [Process The Callback](ob_selfcallbackmerch.html#processing-the-callback) sent to the merchantPostAuthUrl from the ASPSP.
   * You need to retrieve an OAuth token with scope = `openbanking_callback`.
   * Use this token to authenticate when you call the [Forward Payment Callback](ob_paymentcallback.html) endpoint, passing the callback parameters.
   * The payment callback params are passed to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a> at `/tpp/callback`. (See the following section for more on this).   
1. The response to `/tpp/callback` includes the paymentId in the Location Header which you can use to get the most up to date payment status by using [Retrieve Payment](ob_retrievepayment.html).
## Processing the Callback

Note that:

1. Since response parameters are returned in the Redirection URI fragment value, the Client needs to have the User Agent parse the fragment encoded values and pass them on to the Client's processing logic for consumption. (Basically parse the details in JavaScript to post back to your server)
1. Accept the data on your systems.
1. Post the information to the `/payments/callback` [endpoint](ob_paymentcallback.html).

Please see a sample piece of JavaScript code below, which parses the data after the anchor:

	#check for the anchor
	var data = window.location.href.split(#);
	if(data.length < 2) { //just in case not using anchors
	    data = window.location.href.split(?);
	}

	var params = data[1]; 

	var xhr = new XMLHttpRequest();
	xhr.open("POST", YOUR_URL, true);
	xhr.setRequestHeader('Content-Type', 'application/json');
	xhr.send(JSON.stringify({
    		value: params
	}));


This assumes you can accept a `POST` of json to YOUR_URL.

In your logic on the server side, you can parse all the params and submit to the [endpoint](ob_paymentcallback.html).

{% include note.html content="You should ensure that the JavaScript you define works in all browsers for both desktop and mobile and we recommend that you fully test your implementation on all the browsers that you intend to support." %}


{% include links.html %}





