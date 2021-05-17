---
title: Payment Retries
keywords: Payment Retries
summary: "Where a PSU attempts to make a payment but does not complete the full flow, it may be possible to offer the user the option to retry the payment (where it is in a suitable payment status)."
sidebar: ob_sidebar
permalink: ob_paymentretries.html
folder: prodOpenBanking
---

Bank Transfer transactions transition through various payment statuses and in some cases a payment may move to a status from which users are unable to complete their payment. This may happen, for example, where users: 

* Discover that they have insufficient funds on a specific account (and want to choose an account that's held in another bank).
* Lose their Internet connection before approving the payment.
* Have a mobile device that runs out of battery during the payment.
* Etc.

In these cases it is possible to retry the payment, provided:

1. The retry is attempted before the payment's timeout period is exceeded.
1. The payment is in an appropriate status, which allows for a retry.

{% include tip.html content="By default payments timeout after 15 minutes but this time period may be configured per merchant, if required. If you require a specific timeout period please contact your Account Manager." %}

Retries are possible for payments that are in specific statuses, as summarised in the table below:

|**Payment Status**|**Can be Retried?**|
|`PENDING`| Yes|
|`PENDING_APPROVAL`|Yes|
|`DECLINED`|Yes|
|`SETTLEMENT_REJECTED`|Yes|
|`CONSENT_API_REJECTED`|Yes|
|`UNEXPECTED_ERROR`|Yes|
|`UNKNOWN`|No|
|`SETTLEMENT_COMPLETE`|No|
|`PAYMENT_RECEIVED`|No|
|`TIMEOUT`|No|
|`AUTHORISED`|No|
|`SETTLEMENT_PENDING`|No|
|`SETTLEMENT_IN_PROGRESS`|No|
|`OAUTH_CALLBACK_COMPLETE`|No|
|`CONSENT_TIMEOUT`|No|

For more information on these payment statuses, see [Payment Statuses](ob_paymentstatuses.html).

## CHECKOUT & REDIRECT Integrations

The PSU interaction is similar for both the `CHECKOUT` and `REDIRECT` integrations, where a payment retry is possible. 
To illustrate the end user's experience, take the following example:

1. The PSU selects to pay via Bank Transfer.
1. The user selects a bank and is redirected.
1. When reviewing the payment, the PSU decides to cancel before authorising the payment (he/she realises that there are insufficient funds on the account for example).
1. The PSU is redirected to the Nuapay TPP Fail/Cancel screen, with an option to try again: 
<img src="images/ob_retry.png">
1. Once the user clicks **Try Again**, he/she is redirected to the Bank Selection screen (allowing the user to select another bank).


## SELF-HOSTED Integrations

For `SELF-HOSTED` and `SELF-HOSTED-CALLBACK` integrations, merchants/partners will need to programmatically design how they want retries to be handled.

To manage a retry for a given paymentId:

1. Call the Retry Payment API ([Retry Payment](ob_retrypayment.html)).
1. Pass the `paymentId` of the payment that will be retried.
1. The `bankId` is also required - this will be the ASPSP at which the PSU will approve the retried payment.

See [Retry Payment](ob_retrypayment.html) for more details on this service.

{% include links.html %}
