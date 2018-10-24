---
title: Services Overview
keywords: Open Banking Services Overview
summary: "AISP vs PISP - what's the difference?"
sidebar: ob_sidebar
permalink: ob_servicesoverview.html
folder: prodOpenBanking
---

Open Banking currently offers two basic ways for you as a merchant to interact with your clients' bank accounts. You can act as a **PISP** or as an **AISP**. In some cases, and if your business requires it, you can act as both AISP and PISP.

|PISPs|	Payment Initiation Service Providers|
|AISPs|	Account Initiation Service Providers|

## PISP

When acting as a **PISP**, merchants can request clients to make payments via Open Banking.

For end users they:

* Select Open Banking as the payment method on your payment page.
* Select the bank where their account is held.
* Are redirected to this bank's online banking service.
* Verify themselves by providing their online banking credentials (as they would normally do when logging on to their online banking system).
* Select an account from which the payment will be taken (where the customer has more than one account with the bank).
* Confirm the payment amount.
* Are then redirected to the merchant page.

{% include note.html content="Whatever the standard verification and secure customer authentication methods that are normally used to access the customer's online banking portal are applied in the PISP payment flow. Users can feel secure that they are fully in control and are not providing any sensitive details with a third party. " %}

## AISP

Access to account information may be useful for certain businesses where seeing a client's activity on a given account may inform a lending decision, for example. 
AISP access would also be useful in an ERP application that needs to provide real-time views of a number of bank accounts in a single location.   

For end users they:

* Need to confirm the account access request. 
* Are redirected to their bank and must log on.
* Review the requested access and the requested duration.
* Confirm the request.

Once confirmed the requesting organization may handle the account details as required.










