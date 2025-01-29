---
title: Credit Transfer Statuses
keywords: sample
summary: "Credit Transfer transactions move through various statuses in their lifecycle; these are described in this section."
sidebar: ct_sidebar
permalink: np_ctstatuses.html
folder: prodNuapay
---


## Overview

Nuapay supports both standard and express Credit Transfer <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.scheme}}">schemes</a> in both EUR and GBP currencies.
* Standard schemes use a file-based approach to pass payments from Nuapay to the required Scheme for processing.
* Express schemes use REST APIs.
* Standard schemes can take from one to two business days to clear; express payments are processed in seconds.  

{% include note.html content="All merchant/partner interactions with Nuapay are via REST. Where a payment is created against a standard file-based scheme, Nuapay will batch those payments into an appropriate file for onward processing. Your interaction in setting up the payment or retrieving its status later, for example, is all done through APIs. " %}

The following table summarises the differences across the supported CT schemes:

|**Currency**|**Type**|**Scheme**|**Availability**|**Underlying Channel**|**Funds Credited**|
|EUR| Standard| SEPA Credit Transfer|Monday - Friday|File-based (<a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.iso_xml}}">ISO XML file</a>)|Typically 1 business day*|
|EUR| Express| SEPA Credit Transfer Instant|24/7/365|APIs|Instantly|
|GBP| Standard| Bacs Direct Credit|Monday - Friday|File-based (<a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.flat_file}}">flat file</a>)|2 Business Days*|
|GBP| Express | Faster Payments|24/7/365|APIs|Instantly|

|* The SEPA Credit Transfer and the Bacs Direct Credit schemes are subject to non-processing dates throughout the year. See [Non-Processing Days](np_businessdays.html) for more details|

{% include tip.html content="If a SEPA Credit Transfer is created early on a business day (before the cut-off time of 08:00 GMT) the payment will typically be credited to the beneficiary on the same day. Note that Nuapay apply Daylight Savings Time (DST) during the summer months (which is commonly referred to as British Summer Time (BST)). BST runs from the last Sunday in March to the last Sunday in October. During this period the cut off time is actually GMT -1 (so 07:00 GMT); during the period from November to the end of March, the cut off time is 08:00 GMT." %}


## All Credit Transfer Statuses

CT payments transition to different statuses. The statuses vary slightly between _EXPRESS_ and _STANDARD_ schemes:

<img src='images/ct_statuses.png'>

{% include note.html content="Some statuses are only possible in asynchronous processing - these statuses are flagged in the table below." %}


| **Status**                           | **Async?**   | **Description**                                                                                                                                                                                                                                                                                                                                                                         |
|--------------------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `QUEUED`                             | YES         | This status, specific to CT batches, represents the initial state of a batch before the individual CTs are created and validated.                                                                                                                                                                                                                                               |
| `INITIATED`                          | YES         | This is the initial state of a CT created via the asynchronous API. It indicates that the request has been accepted and queued for processing but the actual processing has not yet begun.                                                                                                                                                                                               |
| `PENDING`                            |             | Future-dated payments are initially created in pending status. <br> - Based on the scheme rules for **standard payments**, the CT will transition from this status to READY FOR EXPORT. <br> - Future-dated **Express** payments will transition from this status to PENDING_SETTLEMENT and to ACCEPTED (or REJECTED) on their execution date (at approximately 02:00 GMT).               |
| `PENDING SETTLEMENT`                 |             | This status is applied to Express CTs after they have passed all validation checks and funds have been reserved. The CT is awaiting settlement via the relevant payment scheme.                                                                                                                                                                                                         |
| `READY FOR EXPORT`                   |             | Only applicable for **Standard** schemes: <br> - The standard CT payment has been created. <br> - It has not yet been included in a PAIN.001 XML file (SEPA) or a STD-18 payment file (Bacs).                                                                                                                                                                                             |
| `FAILED`                             | YES         | This status is assigned to a CT that failed to transition from the INITIATED state to a valid subsequent state (e.g., READY_FOR_EXPORT, PENDING_SETTLEMENT) due to validation errors or other processing issues.                                                                                                                                                                         |
| `EXPORTED`                           |             | Only applicable for **Standard** schemes: <br> - The standard CT payment has been included in a PAIN.001 file (SEPA) or a STD-18 file (Bacs) and has been passed to Clearing. <br> - The CT will generally be exported 1 business day prior to the execution date (SEPA) or 2 days in advance (Bacs).                                                                                   |
| `PENDING_SETTLEMENT`                 |             | Only applicable for **Express** schemes: <br> - The payment has been passed to the scheme but has not yet transitioned to `ACCEPTED` or `REJECTED`. <br> - This is an interim status and a payment should only be in this status for a few seconds before transitioning to a final status.                                                                                               |
| `ACCEPTED`                           |             | Where a payment has not been rejected, the CT status is updated to Accepted on its execution date.                                                                                                                                                                                                                                                                                      |
| `REJECTED`                           |             | If the payment cannot be made (e.g., the beneficiary account is closed), the payment will transition to Rejected. <br> - The CT payment will transition to this status where a rejection is processed from the beneficiary bank or from the Scheme. <br> - A CT Rejection results in a credit to the merchant account.                                                                  |
| `RECALLED`                           |             | A **standard** payment has been cancelled prior to being sent to the Scheme for further processing. <br> - A CT payment may be recalled when it is in PENDING or READY FOR EXPORT status. <br> - The Recall operation is available via the Nuapay User Interface (this is not currently an option via the API). <br> - Please contact support should you need to recall a CT payment.        |
| `CANCELLED`                          |             | A **standard** payment has been cancelled AFTER export to the scheme, where the [SEPA Reason Code](np_separeasons.html) is one of the following: `CUST`, `CUTA`, `DUPL`, `UPAY`. <br> - This status is only applicable to SEPA CT payments. <br> - It may not always be possible to cancel an EXPORTED CT payment. <br> - This process requires manual intervention from the Nuapay Support team. |




{% include tip.html content="SEPA and Bacs are file-based schemes and once you have created a set of CT payments for a specific execution date, your transactions are combined into either a PAIN.001 XML file (SEPA) or a Standard-18 (STD-18) flat file format (Bacs) and passed to the appropriate Clearing system for further processing. This is all managed in the background for you and you do not need to interact with these files. They are just referenced here to give some background as to when and why statuses transition, especially from `READY_FOR_EXPORT` to `EXPORTED`." %}



{% include links.html %}
