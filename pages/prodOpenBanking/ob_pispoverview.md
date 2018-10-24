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

## The End-User Experience

Once configured your user will interact with your Open Banking Payment as described below:

1. The user will select the required goods or services.
1. Select **Nuapay Open Banking** as the payment method.
1. Click **Pay**.
1. A pop-up window overlayed on the calling payment page is generated:
<img src = "images/ob_1_selectbnk3.png">
1. The user selects the bank in which his account is held (Barclays for example) and clicks **Continue**.
1. A confirmation of the bank selected is displayed and the user clicks **Confirm**.
1. The user is then redirected to his bank where he must log on with his online banking user name and password:
<img src="images/ob_2_bnklogon.png">
1. Once successfully signed on the user can choose to **Confirm** the payment to the merchant:
<img src ="images/ob_3_bnkconfirm.png">
1. The payment is authorised and the payer is redirected to the merchant site with a confirmation message:
<img src="images/ob_4_conf.png">












