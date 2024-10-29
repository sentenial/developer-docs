---
title: Credit Transfer Cut Off Timing
keywords: sample
summary: "In standard Credit Transfer schemes, transactions are generally processed on the same or next business day depending on the timing. This section outlines the cut off times."
sidebar: ct_sidebar
permalink: np_ctcutoffs.html
folder: prodNuapay
---


## Overview

Nuapay supports the following Credit Transfer schemes:

|**Scheme Name**|**Currency**|
|SEPA CT | EUR|
|FPS |GBP|
|Bacs CT |GBP|

{% include note.html content="All merchant/partner interactions with Nuapay are via REST. Where a payment is created against a standard file-based scheme, Nuapay will batch those payments into an appropriate file for onward processing. Your interaction in setting up the payment or retrieving its status later, for example, is all done through APIs. " %}

## Cut-Off Times

For file-based <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.scheme}}">schemes</a>, like SEPA and Bacs, transactions are combined into files and passed to Clearing for further processing.

Note:
* The schemes have different processing cycles. For SEPA, CT payments are generally processed on the same day or on the next business day.
* For Bacs, payments have a <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.bacs_ct_cycle}}">3-day cycle</a>.
* If you want to ensure that your payment(s) are processed on a specific date you must ensure that you process your payments before the defined cut-off time.

|**Cut-Off Time**: The Cut-Off Time refers to the latest time by which your payment files (SEPA or Bacs Direct Debits and/or Credit Transfers) must be submitted to the Clearing system. Files received before this time will be processed on the next available settlement date. Files submitted after the Cut-Off Time will be processed on the following settlement date. Adhering to these times ensures timely processing of your payments.|

By default, Nuapay has the following CT cut-off times (where D is _today_):

|Scheme| Cut-Off Time| Collection Date|
|SEPA CT| 08:00| D|
|Bacs CT| 21:15| D+2|

These are the latest times by which your payments must be submitted in order to achieve your required collection date.

## Scheme Differences

|**Scheme Name**|**Earliest Export Date**| **Funds Credited**| **Notes**|
|SEPA CT|	On D **before 08:00 GMT**| D| If the transaction/collection is processed **before** 08:00 on a processing day, the CT transaction(s) will generally be processed on the same day: your beneficiary will see the credit on the same day.|
|         | On D **after 08:00** | D+1 | Where the transaction/collection is processed **after** 08:00, the CT transaction(s) will be processed on the next processing day |
|Bacs CT| On D **before 21:15 GMT**|D+2| If the transaction/collection is processed **before** 21:15 on a processing day (DAY 1), the CT transaction(s) will be passed to Bacs with your beneficiary being credited on D+2 (DAY 3).|
|         | On D **after 21:15 GMT**|D+3| If the transaction/collection is processed **after** 21:15 on a processing day, the CT transaction(s) will be passed to Bacs on the next business day, with your beneficiary being credited on D+3.|
|FPS|N/A|D| Because FPS is an Instant scheme, payments are settled within seconds so there are no export timings or restrictions. For future-dated payments, these are processed at 02:00 GMT on the morning of the requested collection date.|


{% include tip.html content="Nuapay apply Daylight Savings Time (DST) during the summer months (which is commonly referred to as British Summer Time (BST)). BST runs from the last Sunday in March to the last Sunday in October. During this period a cut off time of 08:00 is actually GMT -1 (so 07:00 GMT); during the period from November to the end of March, the cut off time is 08:00 GMT." %}
