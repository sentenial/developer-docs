---
title: Cut Off Timing
keywords: Cut Off
summary: "This section outlines the cut off times for Direct Debit and Direct Debit Instructions."
sidebar: np_sidebar
permalink: np_ddcutoffs.html
folder: prodNuapay
---


## Overview

Nuapay supports the following Direct Debit schemes:

|**Scheme Name**|**Currency**|
|SEPA Direct Debit CORE | EUR|
|SEPA Direct Debit B2B | EUR|
|Bacs Direct Debit |GBP|

{% include note.html content="All merchant/partner interactions with Nuapay are via REST. Where Direct Debit payments or  DDIs are created against a standard file-based scheme, Nuapay will batch those payments into an appropriate file for onward processing. Your interaction in setting up payments or DDIs or retrieving their statuses later, for example, is all done through APIs. " %}

## Cut-Off Times

For file-based <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.scheme}}">schemes</a>, like SEPA and Bacs, transactions are combined into files and passed to Clearing for further processing.

Note:
* The schemes have different processing cycles. For SEPA, DD payments are generally passed to Clearing two business days (D-2) ahead of the settlement date (D).
* For Bacs, payments and DDIs have a <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.bacs_ct_cycle}}">3-day cycle</a>.
* If you want to ensure that your payment(s) are processed on a specific date you must ensure that you process your payments before the defined cut-off time.

{% include note.html content="For Bacs, Direct Debit Instructions must be exported to the Bacs scheme (via AUDDIS) and registered with the payer's bank before you can begin to make collections against it. DDIs are exported daily from Nuapay and passed to the scheme. In SEPA, there is no requirement to automatically lodge mandates in this way." %}


|**Cut-Off Time**: The Cut-Off Time refers to the latest time by which your payment files (SEPA or Bacs Direct Debits and/or Credit Transfers) must be submitted to the Clearing system. Files received before this time will be processed on the next available settlement date. Files submitted after the Cut-Off Time will be processed on the following settlement date. Adhering to these times ensures timely processing of your payments.|

By default, Nuapay has the following **Direct Debit** cut-off times:

|Scheme| Cut-Off Time|
|SEPA CORE and B2B | 07:15| 
|Bacs Direct Debit| 19:00| 

**For Bacs DDI**:

|Scheme| Cut-Off Time|
|Bacs AUDDIS| 21:00|

{% include tip.html content="DDI export time will not have any impact on payment processing - any DDIs created *today* before 21:00 will be passed to Bacs today; if there are no AUDDIS rejections, the DDI will move to Active status on D+3." %}


These are the latest times by which your payments/DDIs must be submitted in order to achieve your required execution date.

