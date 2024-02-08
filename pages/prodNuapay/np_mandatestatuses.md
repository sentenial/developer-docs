---
title: Mandate/DDI Statuses
keywords: sample
summary: "Mandate/DDI statuses and how they impact Direct Debit Collection are fully outlined here. "
sidebar: np_sidebar
permalink: np_mandatestatuses.html
toc: false
folder: prodNuapay
---


## Overview

Mandates/DDIs can have various statuses, which are summarised below:

| Status | Description |
|-------|--------|
| `PENDING` | The mandate/DDI has been created but the payer has not signed. Direct Debits cannot be created against the mandate/DDI. |
| `READY_FOR_EXPORT` | **Bacs-only status**; the DDI has been created, the payer has signed but the DDI has not been exported to the AUDDIS service; Nuapay exports DDIs once per day |
| `EXPORTED` | **Bacs-only status**; the DDI has been passed to the AUDDIS service |
| `ACTIVE` | The SEPA mandate has been signed and Direct Debits can be created against it or the DDI has reached Day 5 in the [Bacs cycle](np_mdtoverview.html#auddis-processing-cycle), so payments may now be made against it. |
|`COMPLETE`| Where a once-off mandate/DDI (`mandateType` = `OOFF`) is created, once the single Direct Debit linked to that mandate/DDI is collected, it moves to COMPLETE. No further payments are possible against a mandate/DDI in this status.|
| `CANCELLED` | The mandate/DDI is no longer active. Direct Debit payments cannot be made against a Cancelled mandate/DDI. In Bacs, this status is applied to a DDI after it has been passed to the scheme via an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.auddis}}">AUDDIS</a> submission but has not been approved. Nuapay is notified of the DDI rejection via an AUDDIS response message from the scheme. A DDI may be rejected where the payer's account does not support Direct Debits, for example. Similarly an ACTIVE DDI may be updated to CANCELLED status where the system receives an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.addacs}}">ADDACS</a> file from the Scheme.|
| `UNREADABLE` | If you are using our 3rd party paper mandate/DDI handling and a mandate/DDI is returned by your payer but cannot be clearly read then it is updated to a status of unreadable. |
| `UNSIGNED` | This status is applied if you are using our 3rd party paper mandate/DDI handling service and a mandate/DDI is returned by your payer but has not been signed.|
| `SUSPENDED` | The mandate/DDI is temporarily unusable. Unlike a cancelled mandate/DDI, a suspended mandate/DDI may be re-activated later if required. No Direct Debit payments may be created against a suspended mandate/DDI. Note that you cannot currently suspend a mandate/DDI via the API - this can only be managed via the Nuapay user interface.|

{% include links.html %}
