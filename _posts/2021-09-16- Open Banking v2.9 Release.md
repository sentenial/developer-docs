---
title:  v2.9 Open Banking Released
published: true
permalink: v2.9 Open Banking Release.html
sidebar: productOverview_sidebar
summary: "v2.9 Open Banking Release"
tags: [news]
---


We're pleased to announce our v2.9 Open Banking Release. In this release:

*	STET Changes
	* BNP Bank has implemented elements of the STET 1.4.1 and the 1.4.2 specifications. In this release we have made changes for this particular custom configuration so that we can support payments processed via this ASPSP.
	* BNP Bank also require a custom HTTP Signature in their APIs: additional parameters for `created` and `expires` are required. We have added
support for these values in this release.
* Berlin Group Changes:
  *	Generally `PSU-ID` and `PSU-ID-Type` headers are required when making a payment under the Berlin Group specification. Some ASPSPs vary from the standard however and require a PSU-ID-Type header without a PSU-ID header. In this release we have made changes to support the ASPSPs who are taking this approach.
*	During testing with various ASPSPs (in both the STET and Berlin Group), it was discovered that the Creditor Agent BIC is required in a lot of cases (even though this is not aligned with the specifications). We have made an enhancement in this release to allow for this value to be provided when specific ASPSPs require it.
*	The demo merchant shop has been enhanced in this release: a new frontend has been applied and the shop now supports the [Open Banking & E-Mandate flow](ob_emoverview.html). See the <a href = 'https://api.nuapay.com/merchant/shop' target = "_new"> Merchant Demo Shop</a>.
*	Enhancements have been made to the retry payment functionality in this release: improved internal auditing and the functionality has been refined so that it is not possible to retry where specific [HTTP 4XX codes](ob_httpreasons.html) are returned.
*	A change has been made to allow for QSEAL-encoded PEM certificates in the payment consent call headers in the OBIE scheme. This change means that an Irish ASPSP (PTSB Bank) is now fully supported under the OBIE specification in this release.
*	In the `CHECKOUT` and `REDIRECT` implementations PSUs may see an alert on screen informing them that their account details will be retrieved, as part of their bank transfer payment, to allow for potential refunds later and/or to create a Direct Debit mandate (in the Bank Transfer & E-Mandate flow). We have improved both the text that is displayed and the merchant’s or partner’s ability to manage when that alert is displayed.
