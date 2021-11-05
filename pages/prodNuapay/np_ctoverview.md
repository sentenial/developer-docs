---
title: Credit Transfer Overview
keywords: Credit Transfer Overview
summary: "Credit Transfer payments allow you to push payments to your creditors' accounts via the SEPA CT (SCT) and SEPA Instant CT Schemes (EUR currency) or via Faster Payments or Bacs Direct Credit (for GBP currency)"
sidebar: np_sidebar
permalink: np_ctoverview.html
folder: prodNuapay
---

|Credit Transfers (CTs) are **push** payments: you as the payer _push_ funds to your payee (or beneficiary); in contrast, Direct Debits are **pull** payments: you as the payee _pull_ funds from your payers' accounts, once a mandate (granting you permission to do so) is in place.|

A few points to note in relation to CTs:

* CTs allow you to transfer funds from your account to a beneficiary's account.
* You must have sufficient balance on your account to make the payment.
* You (the merchant) are the payer and the person to whom you are transferring funds is the beneficiary.
* For a SEPA CT generated _today_, the beneficiary's account is generally credited on the following working day (however payments generated prior to 08:00 GMT should be credited on the same day).
* A Bacs Direct Credit generated _today_ will typically be credited to your beneficiary in 2 business days' time.
* Express payments (Faster Payments for GBP; SEPA CT Instant for EUR) are typically credited within seconds.

{% include important.html content="A Note on GMT: Nuapay apply Daylight Savings Time (DST) during the summer months (which is commonly referred to as British Summer Time (BST)). BST runs from the last Sunday in March to the last Sunday in October. During this period the cut off time is actually GMT -1 (so 07:00 GMT); during the period from November to the end of March, the cut off time is 08:00 GMT." type="primary" %}

## Using the Credit Transfer APIs

There are two approachs to CT creation:
1. Before you initiate a CT payment, you create one or more beneficiaries. When you generate a payment, the beneficiary is referenced; this is a 2-step process, requiring two API calls: see [Create Beneficiary](np_createbeneficiary.html) and [Create Credit Transfer](np_createdct.html).
1. You initiate a CT payment where the beneficiary is created **and** the payment is generated; this is a 1-step process, requiring a single API call: [Create Credit Transfer & Beneficiary](np_createctandbene.html).

## Payment Schemes Supported

We currently support the following CT payment schemes:

|**Currency**|**Payment Scheme**|
|EUR|SEPA CT|
|EUR|SEPA Inst CT|
|GBP|Faster Payments|
|GBP|Bacs Direct Credit|

{% include links.html %}
