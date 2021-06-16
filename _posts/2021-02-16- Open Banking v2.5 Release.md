---
title:  v2.5 Open Banking Released
published: true
permalink: v2.5 Open Banking Release.html
sidebar: productOverview_sidebar
summary: "v2.5 Open Banking Release"
tags: [news]
---


We're pleased to announce our v2.5 Open Banking Release.


* UK Open Banking OBIE changes:
  - A change in the OBIE specification (3.1.6) allows TPPs to retrieve the PSU account details as part of the payment consent. This account information may then be used later, if required, to create a refund payment. This is fully supported in this release. (Note that being able to refund payers was already possible for clients with a Nuapay account).
* Berlin Group changes:
  -	As different ASPSPs expect a different set of headers to be signed and reject requests where not all bank-required headers are used, in this release the signature requirements may be configured per ASPSP. 
  - Previously signatures were not provided for Berlin Group API calls to create and retrieve payments. In this release we have enabled signature generation and use the same configuration (as described in the previous point) to decide if the Signature is sent and of which headers it is composed. 
  - Some German ASPSPs require the PSU IBAN and additional information be included in the Payment Request header. This is because the IBAN itself does not determine the user but only an account that can have many users, therefore an additional user ID is needed. We have introduced the ability to pass this PSU-ID as a new header parameter in this release. 
* STET Changes:
  -	Previously we introduced functionality to enable/disable JWS-Signature validations for ASPSP response calls for UK Open Banking. In this release we have added a similar feature for STET-supporting ASPSPs. 
  - It was discovered that a STET-supporting bank was failing to process payments because of URL encoding. As per the OAuth specification, we URL-encode the username and password before Base 64 encoding; this bank expected the URL not to be encoded. To address this we have added a new configuration to allow Admin staff to configure this bank differently to other banks. 
* Nuapay TPP User Interface Updates:
  - Where connectivity issues are detected with an ASPSP, users will now see a pop-up alert informing them that there may be an issue. Because we cannot say definitively that the bank is down, the user will have the option to proceed or perhaps select a different bank. 
  - The Bank Selection screen has been enhanced in this release – a new heading has been added and the alerting has been enhanced where a user’s bank search returns no results.  

