---
title:  v1.10 Open Banking Released
published: true
permalink: v1.10 Open Banking Release.html
sidebar: productOverview_sidebar
summary: "v1.10 Open Banking Release"
tags: [news]
---


We're pleased to announce our v1.10 Open Banking Release.


* During connectivity testing for OBUK it was discovered that certain banks require that a JWS header is not sent but the payload must still be base64-encoded. We have made a change in this release to support this.
* We have introduced an update in this release to better allow Nuapay support/admin staff to investigate failed transactions and see detailed information about TPP-to-ASPSP interactions for particular payments and to help users to determine where a failure occurred. 
* Data Type and label changes:
  - We have refactored some data types in this release; in some cases, for example, a value was incorrectly defined as string rather than number. 
  - An inconsistency in the labelling of an object returned in the response body of the Retrieve Payment History has been resolved in this release: the label ‘data’ is now used rather than ‘events’ as in the previous release. 
* Changes for Euro currency support: 
  - The Sandbox Open Banking shop has been enhanced in this release to include support for the EUR currency.
  - In this release we can now define merchant account per currency at partner or merchant level and the TPP application now populates that account accordingly when calling ASPSPs.
* Where the payment currency is EUR we now require an IBAN to be provided for the PSU account. 

