---
title:  v2.3 Open Banking Released
published: true
permalink: v2.3 Open Banking Release.html
sidebar: productOverview_sidebar
summary: "v2.3 Open Banking Release"
tags: [news]
---


We're pleased to announce our v2.3 Open Banking Release.


* Some minor non-functional security enhancements have been made in this release in response to the findings of our bi-annual security audit.
* Some updates related to Mutual TLS have been made in this release.
  * We do not now reuse a connection where the client certificate differs from the certificate we want to use at the application level.
  * If at the transport level of a connection we use certificate X. Only certificates belonging to the owner of certificate X can be used at the application level.
* Performance enhancements for [List Payments](ob_listpayments.html) and [Retrieve Payment](ob_retrievepayment.html) endpoints have also been carried out in this release.

