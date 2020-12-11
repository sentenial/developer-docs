---
title:  v2.2 Open Banking Released
published: true
permalink: v2.2 Open Banking Release.html
sidebar: productOverview_sidebar
summary: "v2.2 Open Banking Release"
tags: [news]
---


We're pleased to announce our v2.2 Open Banking Release.


* STET-Specific Changes:
  - In the STET implementation it is possible to specify a [future execution date](ob_createpayment.html#setting-an-execution-date) for an Open Banking payment. In this release we have added support to allow merchants/partners to specify this date.
  - We have introduced support for merchants/partners to pass both creditor address and debtor address details in payment requests. This has been introduced as passing these details may be required by certain ASPSPs in certain Open Banking schemes.
  - In STET v1.4.2 the confirmation of the Payment request is introduced as a mandatory step and without it an ASPSP will not finish the payment process: a payment will never reach the `SETTLEMENT_COMPLETED` state. In this release we have updated our TPP to correctly handle any payments to ASPSPs that support v1.4.2 of the STET specification. 
* In this release it is possible for merchants/partners to specify the account into which an Open Banking transaction is [credited](ob_createpayment.html#creditor-accounts).
* We have introduced a new integration type in this release: `REDIRECT`. Similar to the `CHECKOUT` integration, the `REDIRECT` approach is UI based and offers merchants/partners the potential to pass payment links to their PSUs via email or QR codes, for example. See more on this under [Merchant REDIRECT](ob_redirectoverviewmerch.html) and [Partner REDIRECT](ob_redirectoverview.html)
* This v2.2 release also includes a new [Health Check service](ob_healthoverview.html) that enables merchants/partners to retrieve an availability rating for a given ASPSP at any point in time. Where the service returns a poor rating for an ASPSP, the merchant/partner may decide to mark that bank as unavailable on their Bank Selection UI, for example.
