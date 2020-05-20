---
title: Direct Debit Statuses
keywords: sample
summary: "Direct Debits move through various statuses in their lifecycle; these are described in this section. "
sidebar: np_sidebar
permalink: np_ddstatuses.html
folder: product2
---


## Overview

{% include callout.html content="Successfully processed Direct Debits move through the following statuses: READY FOR EXPORT --> EXPORTED --> ACCEPTED" type="primary" %} 

Prior to a Direct Debit (DD) payment being passed to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing system</a> or to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.bacs-clearing}}">Bacs Service</a> it is given a `READY_FOR_EXPORT` status. Nuapay combines Direct Debits into a single payments file prior to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.collection_date}}">collection date</a>. 

When a DD transaction is added to a payment file its status is updated to `EXPORTED` (it is transmitted electonically (exported) to appropriate Clearing mechanism at this point). The DD transaction is exported at least one day before the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.collection_date}}">collection date</a> (for SEPA) and 2 days before for Bacs.

The Clearing channel will dispatch the Direct Debit payments to your payers' banks. If the payers' banks do not reject the Direct Debit payment, Nuapay will update the Direct Debit status to `ACCEPTED` on the collection date. This will generally be the final status of a Direct Debit.


## Pre-Settlement Rejection/Refusal

Should a payer refuse the Direct Debit payment, or if the account is closed, for example, the Bank will reject the payment. In this case the Direct Debit payment will transition from `EXPORTED` to `REJECTED` or `REFUSED`.

These kind of rejections occur **before** the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.collection_date}}">collection date</a> so they are referred to as **Pre-Settlement Rejects**.

{% include note.html content="Pre-settlement Rejects are only possible in SEPA; in Bacs, DD payments cannot be rejected pre-settlement." %}

{% include tip.html content="Rejects, Refusals, Returns and Refunds are collectively referred to as 'R-transactions'" %}


## Post-Settlement Return/Refund

Returns and Refunds can only happen <i>after</i> the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.collection_date}}">collection date</a> and are referred to as Post-settlement R-transactions. 

If Nuapay receives a post-settlement 'R', the Direct Debit status is update from `ACCEPTED` to `RETURNED` or `REFUNDED`.

## Bacs Unpaid Transactions

When a Bacs Direct Debit payment fails i.e. it is not paid by the paying bank, it will be returned unpaid to the service user via the Bacs service using **ARUDD** (Automated Return of Unpaid Direct Debit). Nuapay will update the status of the transaction on receipt of an ARUDD file from Bacs. Returned items will be debited on day 5 or in exceptional circumstances day 6 of the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.bac-collection-cycle}}">Bacs cycle</a>.

For more on the unpaid cycle for Bacs payments please see the Bacs Service User Guide available on the <a href="https://www.bacs.co.uk/" target='_blank'>Bacs site</a>.

## All Direct Debit Statuses

| Status | Description |
|-------|--------|
|`READY_FOR_EXPORT` | The Direct Debit payment has been created but has not yet been included in a PAIN.008 (SEPA) or a STD-18 (Bacs) |
| `EXPORTED` | The payment has been included in a PAIN.008 file (SEPA) or a STD-18 file (Bacs) and has been passed to Clearing. The Direct Debit will generally be exported 2 business days prior to the collection date. The number of days is configurable for SEPA but must be set to 2 for Bacs. |
| `ACCEPTED`	 | If there have been no pre-settlement R-transactions the status is updated to Accepted on the settlement date. |
| `REJECTED` /`REFUSED` / `CANCELLED` | If a pre-settlement R-transaction is processed in Nuapay the status will move from Exported to Rejected/Refused/Cancelled |
| `RETURNED`/`REFUNDED` | Where a Direct Debit is in Accepted status and a post-settlement R-transaction is processed its status will be updated to Returned/Refunded|
| `RE-PRESENTED` | Where a direct debit has been Rejected/Refused/Cancelled/Returned/Refunded you may want to re-try to collect the payment. When you re-present the Direct Debit status is updated to Re-presented and a new Ready-for-Export Direct Debit is generated with a new collection date.|
|`REVOKED`| A Direct Debit that is in READY FOR EXPORT status can be withdrawn before it is dispatched to Clearing so that it isn't processed. In this case the Direct Debit status is updated to REVOKED.|
|`REVERSED` | If you as the merchant have debited funds in error (for example if you have taken a duplicate payment) and want to credit your payer , you can contact your bank to initiate a reversal, The direct debit status is updated to REVERSED and you are debited the funds. A Reversal is a post-settlement status.|
|`PENDING`|The payment is in a pending status. A payment may be in this status where it is created with a mandate and the mandate status is in pending status. |


{% include tip.html content="SEPA and Bacs are file-based schemes and once you have created a set of DD payments for a specific collection date, your transactions are combined into either a PAIN.008 XML file (SEPA) or a Standard-18 (STD-18) flat file format (Bacs) and passed to the appropriate Clearing system for further processing. This is all managed in the background for you and you do not need to interact with these files. They are just referenced here to give some background as to when and why statuses transition, especially from `READY_FOR_EXPORT` to `EXPORTED`." %}



{% include links.html %}
