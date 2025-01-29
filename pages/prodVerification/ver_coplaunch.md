---
title: Initiating a CoP Check
keywords: CoP Checking
summary: "Call CoP to peform an account holder name check for UK accounts."
sidebar: ver_sidebar
permalink: ver_coplaunch.html
folder: prodNuapay
toc: false
---
## Overview

Unlike the [AIS flow](ver_launch.html) flow, there is no Nuapay UI available for calling a CoP check.

Merchants who want to use this service will need to design their own interface, using the [Request Verification](ver_reqverification.html) and [Retrieve Verification](ver_retrieveverification.html) endpoints.

{% include tip.html content="Merchants who have access to the Nuapay User Interface can use the inbuilt CoP check when adding beneficiaries via that channel." %}

To initiate the Verification check via CoP:

* Call the `POST /verifications` endpoint in the Verification Service. ([Request Verification](ver_reqverification.html))
* When making the API call, you must include `ACCOUNT_HOLDER_VERIFICATION` as the `method` and supply the necessary account details within the `verificationData.account` object.

The following are the required parameters:

* `verificationData.account.identification`: this field requires either the IBAN or the sort code and account number, determined by the `schemeName`.
* `verificationData.account.schemeName`: indicates whether the identification is an "IBAN" or "SortCodeAccountNumber".
* `verificationData.account.type`: specifies whether the account is 'BUSINESS' or 'PERSONAL'.
* You can optionally provide the `verificationData.account.secondaryIdentification` parameter for additional account verification. This is used primarily for Building Society accounts.
* The Verification Service will then trigger an asynchronous call to the Nuapay 3rd-party CoP service provider, based on the provided information and the chosen CoP method.
* The service handles the provider's response, storing the CoP results and setting the verification status accordingly.
* Finally, a `201 Created` response is sent back to the `POST /verifications` endpoint, indicating the completion of the request

{% include tip.html content="When testing on the Sandbox environment, use the [CoP Test Data](ver_coptest.html) to simulate the possible responses." %}

See the [Request Verification](ver_reqverification.html) service for more details on the endpoint.
