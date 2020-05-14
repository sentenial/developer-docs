---
title: PISP Implementation Options
keywords: Open Banking PISP Implementation Options
summary: "Payment Initiation Service Provider Checkout Page implementation Options"
sidebar: ob_sidebar
permalink: ob_pispimplementations.html
folder: prodOpenBanking
---

Your PISP checkout page may be implemented in one of the following ways:

1. CHECKOUT
1. SELF_HOSTED
1. SELF_HOSTED_CALLBACK

{% include warning.html content="SELF_HOSTED_CALLBACK mode is currently only available in the Nuapay Test environment." %}

Each implementation option determines whether: 

* You want to use the default Nuapay user interface or implement your own design
* And also allows you to specify how Callback URLs are handled in the PISP flow. 

## What is the Callback URL?

To understand the Callback URL, and how it is used in Nuapay Open Banking, take the following "Happy" flow for an Open Banking payment... 

In an Open Banking payment the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a>:

1. Decides to pay via an account-to-account transfer (an Open Banking payment) and is presented with a list of banks from which to choose.
1. Selects the bank with which he/she holds an account.
1. Is re-directed to the selected bank's online banking system.
1. Logs on to the online banking system as normal and approves the payment.
1. Is automatically logged off from the online banking session (having approved the open banking payment) and is redirected back to the open banking eco system using the callback URL.

The implementation approach you take determines on which URL (defined in the callback) your payer finishes his/her Open Banking payment journey.

## Implementation Overview

The following summarises the options available to both merchants and partners (acting on behalf of merchants):

|**Implementation**|**Details**|
|Checkout|In this mode you use the Nuapay user interface for the Bank Selection screen and the Callback will return the payer to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a>.|
|Self-Hosted| The user interface is handled by you for Bank Selection; callback handling (as in Checkout), is through the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a>.|
|Self-Hosted-Callback| In this mode you handle the user interface and you also manage the Callback URL: the Callback bypasses the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a>. You capture the callback on your platform and post the information back to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a> platform. This option is useful if you want to style your callback handler or have mobile apps handle the callbacks using deeplinking. In the context of mobile apps, deep linking consists of using a uniform resource identifier (URI) that is opened within a mobile app rather than simply launching a web browser.|

<div markdown="span" class="alert alert-info" role="alert"><i class="fas fa-info-circle"></i>  For a good overview and introduction to <b>Deep Linking</b> see this [Wikipedia](https://en.wikipedia.org/wiki/Deep_linking){:target="_blank"} article</div>

Note that it is possible to interact with the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a> as a merchant or as a partner. For a high-level view of the endpoints you need to call, based on your integration, jump to [Quick Start for Partners](ob_quickstartpart.html) or  [Quick Start for Merchants](ob_quickstart.html).

If you think you know the implementation that best suits your needs, select from the options below to dive right in:

|**Mode**|**Implementation**|
|Partner|[Checkout](ob_checkoutoverview.html)|
||[Self-Hosted](ob_selfsetupoverview.html)|
||[Self-Hosted-Callback](ob_selfcallbacksetupoverview.html)|
|Merchant|[Checkout](ob_checkoutoverviewmerch.html)|
||[Self-Hosted](ob_selfsetupoverviewmerch.html)|
||[Self-Hosted-Callback](ob_selfcallbackmerch.html)|



{% include links.html %}
