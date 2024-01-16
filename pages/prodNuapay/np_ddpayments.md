---
title: Direct Debit Payments
keywords: Payments
summary: "Once your mandate is created you can link single Direct Debit or payment schedules to it."
sidebar: np_sidebar
permalink: np_ddpayments.html
folder: prodNuapay
toc: false
---

## Overview

In Direct Debit payments:

* A Direct Debit is linked to a mandate (in SEPA) or to a Direct Debit Instruction - a DDI (in Bacs).
* Direct Debit payments are **pulled** from your payers' accounts on the collection date and credited to your Nuapay merchant account.
* Depending on your business model you may decide to create single Direct Debit payments or, more typically, configure a schedule of recurring payments.
* For more information on Direct Debits see the [Direct Debit Overview](np_ddoverview.html) section.

## Scheme Overview

Every Direct Debit payment must be linked to a mandate or a DDI and every mandate/DDI must be linked to a specific scheme and currency.

Nuapay supports the following Direct Debit schemes:

|**Scheme Name**|**Currency**|
|SEPA CORE| EUR|
|SEPA B2B| EUR|
|Bacs|GBP|

The SEPA scheme is managed by the European Payment Council. In the UK, Bacs is responsible for the Direct Debit scheme.

Both the EPC and Bacs publish guides and rulebooks (which are generally updated on an anual basis) related to how the schemes should be implemented. Nuapay is fully compliant with these rulebooks and constantly monitor and update our Direct Debit solution as required to ensure that we remain fully compliant.


## Scheme Differences

|**Scheme Name**|**Mandate Lodged with Debtor Bank?**|**Earliest Export Date**|**Pre-Settlement R-Transactions Possible?**|**Post-Settlement Return Period**|**Refunds Allowed?**|**Refund Period (Authorised)**|**Refund Period (Unathorised)**|
|SEPA CORE|	No|	D-1|Yes|D+5|Yes|D+8 weeks|D+13 months|
|SEPA B2B|Yes (Manual Process)|D-1|Yes|D+3|No|N/A|N/A|
|Bacs DD|Yes (Automated)|D-2|No|D+3|Yes|No Time limit|No Time limit|

In SEPA any refund that is made within the 8 week period allowed under the SEPA Guarantee is referred to as an Authorised refund; where the refund request is received after 8 weeks of the initial debit (and before 13 months) it is referred for to as an Unauthorised refund.
