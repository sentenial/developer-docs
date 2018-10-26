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

1. The <i>PSU</i> (i.e. end user) will select the required goods or services.
1. Select **Nuapay Open Banking** as the payment method.
1. Click **Pay**.
1. A pop-up window overlayed on the calling payment page is generated. This is rendered through Nuapay's TPP application:<br/>
<img src = "images/ob_1_selectbnk3.png">
1. The user selects the <i>ASPSP</i> (i.e. the bank) in which his account is held (Barclays for example) and clicks **Continue**.
1. A confirmation of the bank selected is displayed and the user clicks **Confirm**.
1. The user is then redirected to his bank where he must sign on with his online banking credentials:
<img src="images/ob_2_bnklogon.png">
1. Once successfully signed on the user can choose to **Confirm** the payment to the merchant:
<img src ="images/ob_3_bnkconfirm.png">
1. The payment is authorised and the payer (PSU) is redirected to the Nuapay TPP with a confirmation message:
<img src="images/ob_4_conf.png">
1. The pop-up window may be closed by the payer (or may close automatically) and the user is redirected to the merchant payment page, with a confirmation message.

{% include callout.html content="On successful completion of this payment flow your customer has provided his/her consent for the payment to be collected for the selected account. The actual funds transfer to your account may happen within a matter of seconds or it may be processed on the following business day. The speed with which funds are transferred to your account is controlled by your customers' banks and is determined by the default payment scheme they are using. A scheme like SEPA CT Instant (for Euro payments) or Faster Payments (for GBP payments) will result in funds being credited to your account within seconds. Schemes like SEPA CT and BACS Credit will generally take a business day to process. Nuapay uses the [Payment Received Webhook](ob_whreceived.html) to notify you when funds are settled to your Nuapay account (Note: only available if you are using a Nuapay account)." type="primary" %}










