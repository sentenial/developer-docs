---
title: Credit Transfer Statuses
keywords: sample
summary: "Credit Transfer transactions move through various statuses in their lifecycle; these are described in this section."
sidebar: np_sidebar
permalink: np_ctstatuses.html
folder: prodNuapay
---


## Overview

Nuapay supports various Credit Transfer schemes: 

|**Currency**|**Type**|**Scheme**|
|EUR| Standard| SEPA Credit Transfer|
|EUR| Express| SEPA Credit Transfer Instant|
|GBP| Standard| Bacs Direct Credit|
|GBP| Express | Faster Payments|

Depending on the scheme being used, the transaction statuses and transitions vary. 

## Express Schemes

In Express schemes:
* Nuapay interacts with Express schemes via REST APIs.
* Funds are credited to the beneficiary account in seconds.
* Operate 24/7/365.
* Transactions are passed to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.csm}}">CSM</a>
* Transactions move from `PENDING` to `ACCEPTED` or `REJECTED`

## Standard Schemes

In standard schemes:
* Nuapay interacts with standard CT schemes via files. The payments created via our API are included in a payment file (XML or <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.flat_file}}">flat file</a>), which is passed to Clearing.
* Funds can take a number of days to reach the beneficiary account (typically the next business day for SEPA CT; two business days for Bacs Direct Credit).
* Transactions typically move from `PENDING` to `READY FOR EXPORT` to `EXPORTED` to `ACCEPTED` or `REJECTED`
  


## All Credit Transfer Statuses

| Status | Description |
|-------|--------|
|`PENDING`|Future-dated payments are initially created in pending status. Based on the scheme rules for standard payments, the CT will transition from this status to READY FOR EXPORT. Future-dated Express payments will transition from this status to ACCEPTED (or REJECTED) on their execution date (at approximately 02:00 GMT) |
|`READY_FOR_EXPORT` | The standard CT payment has been created but has not yet been included in a PAIN.001 XML file (SEPA) or a STD-18 payment file (Bacs) |
| `EXPORTED` | The standard CT payment has been included in a PAIN.001 file (SEPA) or a STD-18 file (Bacs) and has been passed to Clearing. The CT will generally be exported 1 business day prior to the collection date (SEPA) or 2 days in advance (Bacs). |
| `ACCEPTED`	 | The CT status is updated to Accepted on its execution date. |
| `REJECTED` | If the payment cannot be made e.g. the beneficiary account is closed, the payment will transition to Rejected. The CT payment will transition to this status where a rejection is processed from the beneficiary bank or from the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.csm}}">CSM</a>. A CT Rejection results in a credit to the merchant account.|
|`CANCELLED` | A standard payment has been cancelled where the [SEPA Reason Code](np_separeasons.html) is one of the following: `CUST`, `CUTA`, `DUPL`, `UPAY` after being exported to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.csm}}">CSM</a>; this status is only applicable to SEPA CT payments. It may not always be possible to cancel an EXPORTED CT payment and this process requires a manual intervention from the Nuapay Support team to contact the beneficiary bank. Please contact support should you need to cancel a CT payment. |
|`RECALLED` | The payment has been cancelled prior to sending it to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.csm}}">CSM</a> for further processing. A CT payment may be recalled when it is in PENDING or READY FOR EXPORT status. The Recall operation is available via the Nuapay User Interface (this is not currently an option via the API).|


{% include tip.html content="SEPA and Bacs are file-based schemes and once you have created a set of CT payments for a specific execution date, your transactions are combined into either a PAIN.001 XML file (SEPA) or a Standard-18 (STD-18) flat file format (Bacs) and passed to the appropriate Clearing system for further processing. This is all managed in the background for you and you do not need to interact with these files. They are just referenced here to give some background as to when and why statuses transition, especially from `READY_FOR_EXPORT` to `EXPORTED`." %}



{% include links.html %}
