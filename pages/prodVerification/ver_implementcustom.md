---
title: Custom Account Verification UI Flow
keywords: Custom UI Flow
summary: "Steps to Implement a Custom Account Verification UI Flow."
sidebar: ver_sidebar
permalink: ver_implementcustom.html
folder: prodNuapay
toc: false
---
## Overview

If you plan to create your own Account Verification (VOP/CoP) user interface (UI) using the provided APIs, you must follow a defined sequence of steps covering initiation, display, decision capture, and result processing.

## Steps to Implement a Custom Account Verification UI Flow

> 1 - **Check Configuration**

Before starting the verification process, check the configuration at the Originator level to confirm whether Verification of Payee (VOP/CoP) is enabled and required for your specific use case (e.g. Beneficiaries or Credit Transfers).

If the configuration is disabled, the verification flow is not possible.

> 2 - **Initiate Verification**

Call the [Verification Service](ver_reqverification.html) using the `POST /verifications` endpoint.

* **Purpose**:
  Initiates the VOP/CoP check.

* **Required Data**:
  
  Provide:
  * Payee’s name
  * Account identification (IBAN or domestic account details)
  * Account type (mandatory)
  * For non-GB IBANs, include the BIC (note that the **full 11-character BIC is required**)

* **Response**:
  
  The response includes a `uri` pointing to the verification resource (e.g. `/verifications/{verificationId}`).

> 3 - **Launch Custom UI**

The `POST /verifications` API is asynchronous, so after initiating a verification you will need to call the [Retrieve Verification](ver_retrieveverification.html) service using the `verificationId` to obtain the verification result. Typically, the verification completes within a few seconds. Once retrieved, you can launch your custom UI verification flow.

> 4 - **Display Verification Results**

Within your custom UI, display the verification outcome retrieved from the Verification Service.
Your UI must support the following verification statuses:

* Match
* Partial Match / Close Match
* No Match / Not Match
* Unable to Match / Technical Problem
* Wrong Account Type

> 5 - **Capture the User Decision**

Capture the end user’s explicit decision based on the verification outcome — especially when the result is a Partial Match or No Match.

The user may:

* Proceed with the provided name,
* Accept the name suggested by the bank, or
* Cancel the operation.

{% include note.html content="Verification results (VoP/CoP) are advisory only. The user may still choose to proceed with a payment or add a beneficiary even if the verification result is 'No Match'." %}

<!--
> 6 - **Record User Decision**

Your UI must call the `PATCH /verifications/{verificationId}` [endpoint](ver_setconsent.html) immediately after the user makes their decision.

* **Path Parameter**:
  Use the verificationId obtained from Step 2.

* **Payload**:
  Include the `userDecision` parameter.
  
  **Allowed values**:

  * `usedNameEnteredByUser` – User proceeds with the name they originally entered.
  * `usedNameReceivedFromBank` – User accepts the name returned by the bank (relevant for Close Match scenarios).
  * `cancelled` – User cancels the operation.

> 7 - **Retrieve Verification Details**

After the custom UI flow completes (on close), your system must call the `GET /verifications/{verificationId}` [endpoint](ver_retrieveverification.html).

This call retrieves:

* The stored `userDecision`
* The verification ID (exposed as `externalVerificationReference`)
* Other verification metadata
-->
> 8 - **Process and Finalise**

Depending on your use case, use the `verificationId` as required, e.g. to [Create a Beneficiary](np_createbeneficiary.html) or to [Create a Credit Transfer](np_createct.html), linking the verification to the new beneficiary or payment resource.

<!--
Interpret the retrieved verification details and apply the necessary system actions based on the user’s decision:

* If `usedNameReceivedFromBank` was chosen during CT creation:
  * Overwrite the beneficiary profile with the verification result.
  * Update the beneficiary name to match the bank’s suggestion.
* If the user chose to **proceed**:
  * Continue with adding/editing the beneficiary or creating the credit transfer.
* Ensure that the **Verification Result**, including:
  * **Verification ID**, and
  * **Checked By user** details,
    are stored and displayed on relevant screens such as View Beneficiary and View Payment.
-->
