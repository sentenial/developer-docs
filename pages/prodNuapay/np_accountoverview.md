---
title: Nuapay Account Overview
keywords: Nuapay Account Overview
summary: "Every Nuapay merchant is assigned a unique Nuapay International Bank Account - Direct Debit settlements are credited to this account; Credit Transfers are debited from this account."
sidebar: acc_sidebar
permalink: np_accountoverview.html
folder: prodNuapay
---

## Standard Account

You will be provided with your Nuapay IBAN when you register for the Nuapay service.

Our API allows you to carry out various operations on your account:

* View your account
* List all your accounts (if you have more than one)
* View your account balance(s)
* View a specific transaction
* List multiple transactions
* Transfer funds between two of your own Nuapay accounts

## Ledger Accounts

Nupay also provides an optional *Ledger Account* feature. 

Ledger Accounts provide a flexible way to manage and track funds internally without relying on external bank infrastructure. They are especially useful for platforms or merchants that need to allocate, segment, or reconcile balances across different users, use cases, or currencies, while maintaining full control over how and when funds move.

- Ledger Accounts operate similarly to standard accounts in that they:
  - Track and return balances, and allow postings.
  - Have balances calculated and stored at the end of each day, with a running intraday balance that includes the last calculated total plus any intraday activity.

However, unlike standard accounts that may be identified by IBANs:

- Ledger Accounts are **not accessible through the Scheme** (you cannot top them up via Credit Transfer).
- They are identified using an **internal customer reference**.
- Each Ledger Account must have a **unique identifier per merchant**, and a **currency must be specified** at creation.
- Their balances and intraday transactions **roll up into the balance of a parent _Ledger Collective Account_**.


{% include links.html %}
