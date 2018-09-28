---
title: Direct Debit Statuses
keywords: sample
summary: "Direct Debits have the potential to move through various statuses; these are described in this section. "
sidebar: np_sidebar
permalink: np_ddstatuses.html
folder: product2
---


## Overview

{% include callout.html content="Successfully processed Direct Debits move through the following statuses: READY FOR EXPORT --> EXPORTED --> ACCEPTED" type="primary" %} 

Prior to a Direct Debit payment being passed to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing system</a>  it is given a <b>Ready for Export</b> status. Nuapay combines Direct Debits into a single payments file called a PAIN.008 prior to the collection date. 

When a payment is added to a PAIN.008 file its status is updated to <b>Exported</b> (it is exported to Clearing at this point - typically 2 days in advance of the settlement date).

The SEPA Clearing channel will dispatch the Direct Debit payments to your payers' banks. If the debtor bank do not reject the Direct Debit payment, Nuapay will update the Direct Debit status to <b>ACCEPTED</b> on the collection date. This will generally be the final status of a Direct Debit.

## Pre- and Post-Settlement Rejects

Should a payer refuse the Direct Debit payment or if there are insufficient funds to meet the requested amount, for example, the Bank will reject the payment. In this case the Direct Debit payment will not be in an ACCEPED status. This rejection is notified to Nuapay and the Direct Debit status is updated to <b>REJECTED</b> or <b>REFUSED</b>. These rejections occurs <i>before</i> the settlement date so they are referred to as Pre-Settlement Rs.

In some cases however (on average 5% of all your Direct Debits) your payers' bank or your payers may return or lodge a refund against your Direct Debit. Returns and Refunds can only happen <i>after</i> the collection day and are referred to as Post-settlement Rs. If Nuapay receives a post-settlement R, the Direct Debit status is update from ACCEPTED to <b>RETURNED</b> or <b>REFUNDED</b>.


## All Direct Debit Statuses

| Status | Description |
|-------|--------|
|READY_FOR_EXPORT | The Direct Debit payment has been created but has not yet been included in a PAIN.008 |
| EXPORTED | The payment has been included in a PAIN.008 file and has been passed to SEPA Clearing. The Direct Debit will generally be exported 2 business days prior to the collection date. The number of days is configurable. |
| ACCEPTED	 | If there have been no pre-settlement R-transactions the status is updated to Accepted on the settlement date. |
| REJECTED /REFUSED / CANCELLED | If a pre-settlement R-transaction is processed in Nuapay the status will move from Exported to Rejected/Refused/Cancelled |
| RETURNED/REFUNDED | Where a Direct Debit is in Accepted status and a post-settlement R-transaction is processed its status will be updated to Returned/Refunded|
| RE-PRESENTED | Where a direct debit has been Rejected/Refused/Cancelled/Returned/Refunded you may want to re-try to collect the payment. When you re-present the Direct Debit status is updated to Re-presented and a new Ready-for-Export Direct Debit is generated with a new collection date.|
|REVOKED| A Direct Debit that is in READY FOR EXPORT status can be withdrawn before it is dispatched to Clearing so that it isn't processed. In this case the Direct Debit status is updated to REVOKED.|
|REVERSED | If you as the merchant have debited funds in error (for example if you have taken a duplicate payment) and want to credit your payer , you can contact your bank to initiate a reversal, The direct debit status is updated to REVERSED and you are debited the funds. A Reversal is a post-settlement status.|
|PENDING|The payment is in a pending status. A payment may be in this status where it is created with a mandate and the mandate status is in pending status. |


{% include links.html %}
