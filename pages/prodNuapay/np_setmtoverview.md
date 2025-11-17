---
title: Settlement Overview
keywords: Nuapay Settlement Overview
summary: "Settlement is the term applied to the process that sweeps funds from your Nuapay account to your High-Street bank account. Use the settlement APIs to retrieve details of the makeup of these settlements."
sidebar: acc_sidebar
permalink: np_setmtoverview.html
folder: prodNuapay
---

## Settlements

It is possible to configure your Nuapay account in various modes:

* Set to **D** : funds are credited to your high-street bank account on **the value date (D)** of any Direct Debits or incoming Credit Transfers that have been credited to your account.
* Set to **D Plus**: funds are credited to your high-street bank account on a **configured number of days AFTER (D+)**.
* Set to **Self Managed**: funds are manually disbursed by you to the required beneficiary account(s).   

For clients who are on *D* and *D Plus* it is possible to retrieve the details of the settlements generated:

* Call the [List Account Settlements](np_listaccountsetmts.html)
* Call the [Retrieve Account Settlement](np_retraccountssetmt.html)



