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
| `PENDING` | (Relevant for [CHECKOUT](ob_pispimplementation.html#checkout-mode) mode only) The payment has been created: the merchant has initiated the `POST/payments` call but the PSU has not yet selected the required bank.   | No | No | N/A |
| `CONSENT_API_REJECTED` | There was a technical issue at the ASPSP; no further processing will be possible.| Yes | No | N/A |
| `PENDING_APPROVAL` | The approval for the payment is pending: the PSU has not yet approved the payment on the ASPSP.| No | No | N/A |
| `OAUTH_CALLBACK_COMPLETE` | The ASPSP has informed Nuapay that the payment has been authorised/declined by the PSU | No | No | N/A |
| `AUTHORISED` | The PSU has authorised the payment on the ASPSP. | No | No | N/A |
| `DECLINED` | The PSU has declined the payment on the ASPSP. | Yes | No | N/A |
| `SETTLEMENT_PENDING` | The payment has been authorised but has not yet transitioned to `SETTLEMENT_IN_PROGRESS` status. | No | No | N/A |
| `SETTLEMENT_IN_PROGRESS` |The settlement is being processed by the ASPSP. The payment will generally move to `SETTLEMEMT_COMPLETE` after this status. For high value goods we recommend to wait for a final status before processing the order. | No | Yes | [PaymentInProgress](ob_whpaymentinprogress.html) |
| `SETTLEMENT_COMPLETE` | The payment has settled (funds have been credited to the merchant account). This is a Final status; the merchant may ship goods. | Yes | Yes | [PaymentCompleted](ob_whpaymentcomplete.html) |
| `SETTLEMENT_REJECTED` | The settlement has not been completed and won’t be in future. This is a Final status; the merchant should not ship goods. | Yes | Yes | [PaymentRejected](ob_whpaymentrejected.html) |
| `TIMEOUT` |The payment timed out - this may happen where the user fails to authorise the payment on the ASPSP within the allowed timeout period, for example. | Yes | Yes | [PaymentTimeout](ob_whpaymenttimeout.html)  |
| `CONSENT_TIMEOUT` |The PSU provided his/her consent but the merchant-defined timeout period has elapsed. No payment will be attempted. | Yes | Yes | [PaymentTimeout](ob_whpaymenttimeout.html) |
| `UNEXPECTED_ERROR` |A processing error has occurred. No payment will be completed. | Yes | No | N/A |


{% include links.html %}






