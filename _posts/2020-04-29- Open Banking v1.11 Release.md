---
title:  v1.11 Open Banking Released
published: true
permalink: v1.11 Open Banking Release.html
sidebar: productOverview_sidebar
summary: "v1.11 Open Banking Release"
tags: [news]
---


We're pleased to announce our v1.11 Open Banking Release.


* It is now possible to define the local payment instrument to use in an open Banking payment, previously payments were defaulted to use Faster Payments.
* The payment audit service has been extended in this release to include token interactions between the TPP and ASPSPs.
* We have introduced a new integration type in this release: `SELF_HOSTED_CALLBACK`. Previously only two integrations were possible (`CHECKOUT` or `SELF_HOSTED`). With `SELF_HOSTED_CALLBACK`, the `merchantPostAuthUrl` that is provided in the request body is actually the callback URL that the Partner/Merchant expects the PSU to be redirected to from the ASPSP. 
* Two new services have been added in this release:
  - POST /applications - allows TPPs, Partners and Merchants to configure OBUK Software Statements that were added in the Open Banking Directory. Note that Application and Software Statement are synonymous.
  - POST /payments/callback - allows merchants or partners to pass callback parameters that the TPP should use after an ASPSP redirect.
* To support clients that will look to use the new `SELF_HOSTED_CALLBACK` integration, we have expanded the POST /aspsps/aspspId/register service so that the system now validates that the Software Statement that is being used for registration exists in the TPP application. Also, after registration, all Client Details stored must be referenced in the Application/Software Statement that has been registered.
