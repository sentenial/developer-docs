---
title:  v2.1 Open Banking Released
published: true
permalink: v2.1 Open Banking Release.html
sidebar: productOverview_sidebar
summary: "v2.1 Open Banking Release"
tags: [news]
---


We're pleased to announce our v2.1 Open Banking Release.


* We have made specific updates in this release to enhance our support for the Berlin Group specification:
  - The ASPSP callback is now processed for the REDIRECT flow in both TPP Callback and Merchant Callback case for Berlin-Group ASPSPs.
  - The GET /payment has been enhanced in this release to support Berlin Group integrations.
  - When calling to Berlin-Group ASPSPs the TPP-Redirect-URI is now always passed.
  - We have added support in this release for processing ASPSP payment callback using the Berlin Group API OAuth2 approach.
  - It is now possible to process payments with ASPSPs using the Berlin Group API - Implicit OAuth2SCA Approach.
  - In this release we have made an update to the GET / banks service to include a new field in the response to indicate if the debtor account is required when initiating PISP requests later against that ASPSP (OBUK-2084). 
  - In the TPP UI we have enhanced ASPSP filtering due to the requirement of the 'debtor account' field for Berlin Group integrations. 
* The following changes were made to improve our STET specification support:
  - SHARED_SECRET authorization type was not supported by the STET Implementation in the previous release; this is now available in v2.1.
  - The `STETMilliseconds` is not accepted in the dateTime fields so we have added configuration to handle this (BNP Parisbas, for example, rejects `2020-07-09T12:32:11.123Z` but will accept `2020-07-09T12:32:11Z`).
  - The Credit Mutuel Date header value was not being provided in a valid HTTP Date format. We have addressed how to handle this issue in this release. 
  - We have introduced the capability of handling Local Instrument in the payment request for STET in this release (and this fix also has an impact for the Berlin Group specification) (OBUK-2167).  
* The merchant stub has been updated to now support the Berlin Group specification.
* We have addressed an issue in this release where we failed to send payment consent request due to some APSPs rejecting our iat claim timestamp.
* In addition to the previous item, we have also added support to allow for time drift when validating iat timestamps for incoming timestamps.
* We have introduced the ability to configure ASPSP-specific API configurations for the static request headers/values the bank may expect the Nuapay TPP to send.

