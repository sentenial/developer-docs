---
title:  v2.0 Open Banking Released
published: true
permalink: v2.0 Open Banking Release.html
sidebar: productOverview_sidebar
summary: "v2.0 Open Banking Release"
tags: [news]
---


We're pleased to announce our v2.0 Open Banking Release.


* This version introduces a major technical refactoring of the TPP application. This work was required as we look to expand our support from the OBUK scheme to other Open Banking specifications (STET and Berlin Group).
* A new User Interface design has been implemented in this release.
* We have added support for the STET PSD2 API specification in this release:
  - We have introduced a PISP service integration for French banks that uses the STET PSD2 API specification.
  - STET has defined various iterations of its specification; in this release we support STET PSD2 API versions 1.4.0, 1.4.1 and 1.4.2. 
  - We now process ASPSP callback for the REDIRECT flow in both TPP Callback and the Merchant Callback case. Based on the callback we will either reject, keep the payment in progress, or complete the payment processing.
  - We have introduced some changes to our ASPSP stub to support the STET PSD2 API specification.
  - We have implemented a mechanism to regularly retrieve the status of payments that are in progress under the STET PSD2 API specification: ASPSPs are queried for any payment that has not been processed (and is in `SETTLEMENT_IN_PROGRESS` status).
* In this release the ASPSP and Merchant stubs have been updated to allow customer to properly simulate the `SELF_HOSTED_CALLBACK` integration type (introduced in the previous release) and payment statuses transition, including the `PAYMENT_RECEIVED` status.

