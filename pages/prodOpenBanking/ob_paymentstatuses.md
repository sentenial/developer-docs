---
title: Payment Statuses
keywords: Payment status open banking transitions
summary: "Open Banking payments transition through various statuses through their lifecycle. This section describes each of these statuses and the Webhooks that may be generated as statuses transition."
sidebar: ob_sidebar
permalink: ob_paymentstatuses.html
folder: prodOpenBanking
toc: false
---

## Overview

Open Banking Payments transition from an initial `PENDING` to any one of a number of possible statuses. 

The following gives an overview of each status and, if applicable, the Webhook event triggered:

| **Status Name** | **Description** | **Final Status?** | **Webhook Triggered?** | **Webhook Name** |
| `PENDING` | [Relevant for [Checkout](ob_pispimplementation.html#checkout-mode) mode only] The payment has been created: the merchant has initiated the `POST/payments` call but the PSU has not yet selected the required bank.   | No | No | N/A |
| `CONSENT_API_REJECTED` | There was a technical issue at the ASPSP; no further processing will be possible.| Yes | Yes | [PaymentRejected](ob_whpaymentrejected.html) |
| `PENDING_APPROVAL` | The approval for the payment is pending: the PSU has not yet approved the payment at the ASPSP.| No | No | N/A |
| `OAUTH_CALLBACK_COMPLETE` | The ASPSP has informed Nuapay that the payment has been authorised/declined by the PSU | No | No | N/A |
| `AUTHORISED` | The PSU has authorised the payment at the ASPSP. | No | No | N/A |
| `DECLINED` | The PSU has declined the payment at the ASPSP. | Yes | Yes |[PaymentRejected](ob_whpaymentrejected.html)|
| `FUNDS_CHECK_TIMEOUT` | The response to the funds check is later than the configured timeout. | Yes | No |N/A|
| `FUNDS_CHECK_FAILED` | The funds check has indicated that there are insufficient funds to complete the payment. | Yes | No |N/A|
| `FUNDS_CHECK_PASSED` | Sufficient funds are available to complete the payment. | No | No |N/A|
| `SETTLEMENT_PENDING` | The payment has been authorised but has not yet transitioned to `SETTLEMENT_IN_PROGRESS` status. | No | No | N/A |
| `SETTLEMENT_IN_PROGRESS` |The settlement is being processed by the ASPSP. The payment will generally move to `SETTLEMEMT_COMPLETE` after this status. For high value goods we recommend waiting for a final status before processing the order. | No | Yes | [PaymentInProgress](ob_whpaymentinprogress.html) |
| `SETTLEMENT_COMPLETE` | The ASPSP has debited the payment from the PSU's account. This may be treated as a Final status if the merchant does not have a Nuapay account; in this case, the merchant should confirm the crediting of its account before shipping the goods. | Conditional | Yes | [PaymentCompleted](ob_whpaymentcomplete.html) |
| `SETTLEMENT_REJECTED` | The settlement has not been completed and won’t be in the future. This is a Final status; the merchant should not ship the goods. | Yes | Yes | [PaymentRejected](ob_whpaymentrejected.html) |
| `PAYMENT_RECEIVED` | The settlement amount has been credited to the merchant's Nuapay account. | Yes | Yes | [PaymentReceived](ob_whreceived.html) |
| `TIMEOUT` |[Relevant for [Checkout](ob_pispimplementation.html#checkout-mode) mode only] The payment timed out - this may happen where the user fails to progress to the ASPSP from the TPP before the merchant-configured time-out period. This could happen, for example, if the user has not selected an option on the Bank Select screen within the required time period.  | Yes | Yes | [PaymentTimeout](ob_whpaymenttimeout.html)  |
| `CONSENT_TIMEOUT` |The PSU provided his/her consent but the merchant-defined timeout period has elapsed. No payment will be attempted. | Yes | Yes | [PaymentTimeout](ob_whpaymenttimeout.html) |
| `PAYMENT_REVERSED` |A payment that was previously received is credited back to the PSU. A payment is typically reversed where the merchant deems it appropriate to refund a customer (following a complaint, for example). | Yes | Yes | [PaymentReversed](ob_whrreversed.html) |
| `PAYMENT_REVERSAL_REJECTED` |A payment credited to the PSU has been rejected by the beneficiary bank for a specific reason (e.g. the account is closed). | Yes | No | N/A |
| `UNEXPECTED_ERROR` |A processing error has occurred. This may be due to connectivity issues between ASPSP and the TPP for example. | Yes | No | N/A |
| `UNKNOWN` |The ASPSP is unavailable (HTTP 500 response) and the current payment status cannot be determined  | No | No | N/A |



{% include links.html %}






