---
title: Mandate Statuses
keywords: sample
summary: "Mandate statuses and how they impact Direct Debit Collection are fully outlined here. "
sidebar: np_sidebar
permalink: np_mandatestatuses.html
toc: false
folder: product2
---


## Overview

Mandates can have various statuses, which are summarised below. Note that a number of additional statuses are possible (SCREENING, COMPLETE, etc.) but are not relevant to Nuapay users and can be ignored.

| Status | Description |
|-------|--------|
| PENDING | The mandate has been created but the payer has not signed. Direct Debits cannot be created against the mandate. |
| ACTIVE | The mandate has been signed and Direct Debits can be created against it. |
| CANCELLED | The mandate is no longer active. Direct Debit payments cannot be made against a Cancelled mandate. |
| UNREADABLE | If you are using our 3rd party paper mandate handling and a mandate is returned by your payer but cannot be clearly read then it is updated to a status of unreadable. |
| UNSIGNED | This status is applied if you are using our 3rd party paper mandate handling service and a mandate is returned by your payer but has not been signed.|
| SUSPENDED | The mandate is temporarily unusable. Unlike a cancelled mandate, a suspended mandate may be re-activated later if required. No Direct Debit payments may be created against a suspended mandate. Note that you cannot currently suspend a mandate via the API - this can only be managed via the Nuapay user interface.|


{% include links.html %}
