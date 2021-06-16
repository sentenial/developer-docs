---
title:  v2.6 Open Banking Released
published: true
permalink: v2.6 Open Banking Release.html
sidebar: productOverview_sidebar
summary: "v2.6 Open Banking Release"
tags: [news]
---


We're pleased to announce our v2.6 Open Banking Release.

* Endpoint Updates:
  - The GET /banks service has been enhanced to support country filtering. 
  - GET/organisations now returns merchant e-mail and phone number. 
* In this release it is possible to better control when the Bank Confirmation screen is rendered (in Desktop/Mobile mode) for CHECKOUT integrations. 
* The automated process, which performs a clean-up task to find payments in PENDING status and updates their status to TIMEOUT, is now considered as a trigger for the Timeout Webhook.
* Previously where a PSU initiated a payment and cancelled out of the flow, that payment could not be retried. In this release, in certain scenarios, a PSU may now retry payments.
* Following on from the previous change, in `CHECKOUT` and `REDIRECT` modes, PSUs may now recover their payment from various statuses. We have made the required changes in both the logic and the user interface to support the PSU’s journey. 
* An improvement has been made to the notification text displayed during the QR Code authorisation flow.
