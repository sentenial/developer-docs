---
title:  v2.4 Open Banking Released
published: true
permalink: v2.4 Open Banking Release.html
sidebar: productOverview_sidebar
summary: "v2.4 Open Banking Release"
tags: [news]
---


We're pleased to announce our v2.4 Open Banking Release.

|**Note**| The following changes are scheduled to be available on the Sandbox environment in late January 2021.|

* This release includes a new QR-Code-driven decoupled-SCA approval method for **CHECKOUT** and **REDIRECT** integrations. This allows PSUs to initiate their open banking payment on the desktop and authorise the payment (using biometrics, for example) on a mobile device. 
* UK Open Banking OBIE changes:
  * The Open Banking UK specification, OBIE 3.1.6, is now supported in this release. 
  * In this release it is possible for merchants/partners to provide the creditor account as an IBAN in UK Open Banking; previously only Sort Code and Account Number were possible.
* Berlin-Group Changes
  * The scaRedirect flow is now supported 
  * When connecting to a Berlin-Group ASPSP, PSU account details are required and in this release, users are prompted to supply their details via the TPP User Interface (in the **CHECKOUT** and **REDIRECT** flows).
* The [List Payments](ob_listpayments.html) and [List Refund Payments](ob_refundpaymentlist.html) endpoints have been enhanced in this release to allow for additional filters on amount and create date.
* When the **REDIRECT** integration was added (in v2.2), we introduced the concept of the `UIID`. In this release we have made it possible for **CHECKOUT** users to also optionally use this identifier (rather than the `paymentId`). 
* It is now possible to pass the customer IP address in the [Create Payment](ob_createpayment.html) endpoint. 
* This release also includes a new [Bank Status Check Service](ob_healthoverview.html) that enables merchants/partners to retrieve an availability rating for a given ASPSP at any point in time. Where the service returns a poor rating for an ASPSP, the merchant/partner may decide to mark that bank as unavailable on their Bank Selection UI, for example.
