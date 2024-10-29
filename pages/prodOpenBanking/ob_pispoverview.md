---
title: Payment Initiation Overview
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

* No need to key in credit card, expiry and CVV details.
* Card limits are not applicable.
* Added confidence that the payment is secure as the actual authorisation takes place on the user's online banking portal.
* Potential for card details to be stolen or hacked is eliminated.
* The merchant doesn't hold any of your personal financial details.

<img src = 'images/pisp_advantages.png'>


## Implementations

Nuapay supports the following implementation options:

* Redirect
* Self-Hosted
* Self-Hosted-Callback
* <p style="color: #d3d3d3;">Checkout</p>

{% include tip.html content="If you want to use the Nuapay User Interface we recommend that you use the `Redirect` option. The `Checkout` mode also uses the Nuapay UI but you may encounter some issues with this integration mode on some mobile devices." %}

These implementation modes are described in greater details in [PISP Implementation Options](ob_pispimplementations.html).
