---
title: PISP Overview
keywords: Open Banking PISP Overview
summary: "Payment Initiation Service Provider mode"
sidebar: ob_sidebar
permalink: ob_pispoverview.html
folder: prodOpenBanking
---

Initiating payments via Open Banking offers numerous benefits.

## Advantages

**For Merchants**

* Open Banking charges are much lower than a card payment.
* No PCI-DSS requirements.
* No sensitive customer data is ever transmitted or stored on your server.


**For your clients**

* No need to key in credit card, expiry and CVV numbers.
* Card limits are not applicable.
* Added confidence that the payment is secure as the actual authroisation takes place on the user's online banking portal.
* Potential for card details to be stolen or hacked is eleminated.
* The merchant doesn't hold any of your personal financial details.

## Implementations

Nuapay supports the following implementation options: 

* Checkout 
* Self-Hosted 
* Self-Hosted-Callback

These implementation modes are described in greater details in [PISP Implementation Options](ob_pispimplementation.html).

{% include warning.html content="SELF_HOSTED_CALLBACK mode is currently only available in the Nuapay Test environment." %}










