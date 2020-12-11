---
title:  v1.9 Open Banking Released
published: true
permalink: v1.9 Open Banking Release.html
sidebar: productOverview_sidebar
summary: "v1.9 Open Banking Release"
tags: [news]
---


We're pleased to announce our v1.9 Open Banking Release.


* New services have been introduced for:
  - [List Refund Payments](ob_refundpaymentlist.html)
  - [Retrieve Refund](ob_refundpaymentview.html)
  - [List Payments](ob_listpayments.html)
* The payment response now includes a Link object; this object has been added to the following services: 
  - POST /payments 
  - GET /payments/{paymentId} 
  - PATCH /payments/{paymentId} 
* In the previous version, the payment reference displayed on the user interface was always the end-to-end reference. In this release the reference that is displayed is now based on the currency being used. 
* Support for more than one certificate type (e.g. eIDAS and OBUK) has been added in this release. 
* A new configuration  (Claims Excluded From Jws Signature Jose Header) has been added in this release allowing ASPSPs to be configured depending on their individual JOSE Header requirements. 
* A new Webhook [PaymentRefundRejected](ob_whrefundrejected.html)has been introduced in this release. See section 4.6 on page 9.
