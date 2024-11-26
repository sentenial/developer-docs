---
title: ISO & SWIFT Reason Codes
keywords: Application Reason Codes
summary: "When processing transactions via file, a number of application errors are possible: these are sometimes referred to as Technical Errors and are generated prior to payments being passed to Clearing for further processing"
sidebar: resources_sidebar
permalink: np_isoreasons.html
folder: prodNuapay
toc: false
datatable: true
---

The following are possible when processing FPS transactions:

<div class="datatable-begin"></div>

Code       | Description                                                                  
---------- |  ----------------------------------------------------------------------------
AC03	     | Creditor account number invalid or missing
AC05	     | Closed Debtor Account Number
AC07	     | Beneficiary account closed
AC09	     | Account is not in the currency quoted
AC12	     | Account type missing or invalid
AG01	     | Transaction forbidden on this account for regulatory reasons.
AG03	     | Transaction type not supported/authorized on this account
AM08	     | Invalid charges amount
AM09	     | Amount received is not the amount agreed or expected
AS01	     | Account transferred
BE01	     | Inconsistent With End Customer
BE03	     | Unknown Bank
BE08	     | Debtor name is missing
BE09	     | Country code is missing or Invalid
CUTO	     | Passed payment cut-off time
IP01	     | Sending FPS Institution action required
IP02	     | Return requested by sender of original payment
MS01	     | Not specified reason
PR01	     | Payment rejected, missing payee reference
PR02	     | Payment rejected incorrect payee reference
PY01	     | Unknown BIC in routing table
RC02	     | Invalid Bank Identifier
RC03	     | Invalid Debtor Bank Identifier
RC04	     | Invalid Creditor Bank Identifier

<div class="datatable-end"></div>


{% include links.html %}
