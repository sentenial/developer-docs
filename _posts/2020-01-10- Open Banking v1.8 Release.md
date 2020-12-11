---
title:  v1.8 Open Banking Released
published: true
permalink: v1.8 Open Banking Release.html
sidebar: productOverview_sidebar
summary: "v1.8 Open Banking Release"
tags: [news]
---


We're pleased to announce our v1.8 Open Banking Release.


* In the previous release where further processing was not possible (e.g. due to a technical issue), the error messaging was not presented very well; this has been improved in this release. 
* In this release we added the ability to configure the Base64 implementation per ASPSP. 
* We have introduced payment matching where a merchant is using a Nuapay account and where a payment is credited to that account. The payment now moves to `PAYMENT_RECEIVED` [status](ob_paymentstatuses.html) once the payment credits the Nuapay account. 
* A new service, allowing merchants to initiate refund payments, is available in this release: [Refund Payment](ob_refundpayment.html)
* New [Webhooks](ob_whoverview.html) have been added in this release notifying configured clients of an: 
  - Authorised Payment
  - Declined Payment 
  - Refunded Payment 
  - Refund Successful
* Payment references are now either merchant-specified or system-generated. The payment reference goes end-to-end and allows transactions to be matched to the required Nuapay account (where merchants are using a Nuapay merchant account). 
* Finally, an internal change has been introduced in this release to streamline the registration of new ASPSPs. These changes will allow Nuapay’s internal support staff to quickly on-board new banks on the system. 


