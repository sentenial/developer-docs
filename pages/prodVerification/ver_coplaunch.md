---
title: Initiating a Payee Check
keywords: Payee Checking
summary: "Call CoP or VoP to peform an account holder name check on your payee account."
sidebar: ver_sidebar
permalink: ver_coplaunch.html
folder: prodNuapay
toc: false
---
## Overview

Unlike the [AIS flow](ver_launch.html) flow, there is no Nuapay UI available for calling a CoP or VoP check.

Merchants who want to use this service and design their own interface, see [Implementing a Custom Account Verification Flow](ver_implementcustom.html).

{% include tip.html content="Merchants who have access to the Nuapay User Interface can use the inbuilt CoP/VoP check when adding beneficiaries via that channel." %}

## To initiate the Verification check:

* Call the `POST /verifications` endpoint in the Verification Service. ([Request Verification](ver_reqverification.html))
* When making the API call, you must include `ACCOUNT_HOLDER_VERIFICATION` as the `method` and supply the necessary account details within the `verificationData.account` object.
* For **CoP**:
  * Set the `schemeName` = `SortCodeAccountNumber` (or you may use `IBAN` if required).
  * Set `identification` to the concatenation of the Sort Code and Account Number. 
* For **VoP**:
  * Set the `schemeName` = `IBAN`.
  * A `bic` must also be provided.

{% include tip.html content="BIC values can be either 8 or 11 characters long. VoP requires the full 11-character BIC. If only an 8-character BIC is available, append 'XXX' to the end." %}

The following are the required parameters:

* `verificationData.account.identification`: this field requires either the IBAN or the sort code and account number, determined by the `schemeName`.
* `verificationData.account.schemeName`: indicates whether the identification is an "IBAN" or "SortCodeAccountNumber".
* `verificationData.account.type`: specifies whether the account is `BUSINESS` or `PERSONAL`.
* You can optionally provide the `verificationData.account.secondaryIdentification` parameter for additional account verification. This is used primarily for Building Society accounts in CoP requests.
* The Verification Service will then trigger an asynchronous call to the Nuapay 3rd-party verification service provider, based on the provided information and the chosen CoP/VoP method.
* The service handles the provider's response, storing the results and setting the verification status accordingly.
* Finally, a `201 Created` response is sent back to the `POST /verifications` endpoint, indicating the completion of the request

{% include tip.html content="When testing on the Sandbox environment, use the [Verification Test Data](ver_coptest.html) to simulate the possible responses." %}

See [Implementing a Custom Account Verification Flow](ver_implementcustom.html) for more details on the overall flow and sequence of API requests.
