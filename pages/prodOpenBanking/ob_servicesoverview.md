---
title: Services Overview
keywords: Open Banking Services Overview
summary: "AISP vs PISP - what's the difference?"
sidebar: ob_sidebar
permalink: ob_servicesoverview.html
folder: prodOpenBanking
---

Open Banking allows merchants to interact with their clients' bank accounts, in order to:  

* Initiate payments.

  OR

* Make account access requests.

## Third-Party Provider

Nuapay is a Third Party Provider (<a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.tpp}}">TPP</a>).

As a TPP, Nuapay:

* Facilitates the interaction between the `Merchant`, the merchant's `User` (also referred to as a <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a>) and the PSU's `bank` (also referred to as the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>).
* Acts in two modes: as a Payment Initiation Service Provider (`PISP`) or as an Account Initiation Service Provider (`AISP`).

## PISP

When acting as a **PISP**, merchants can request clients to make payments via Open Banking.

For end users they:

* Select Open Banking as the payment method on your payment page.
* Select the bank where their account is held.
* Are redirected to this bank's online banking service.
* Verify themselves by providing their online banking credentials (as they would normally do when logging on to their online banking system).
* Select an account from which the payment will be taken (where the customer has more than one account with the bank).
* Confirm the payment amount.
* Are then redirected to the merchant's confirmation page.
* The PSU account is debited and the merchant account is credited.

{% include note.html content="Whatever the standard verification and secure customer authentication methods that are normally used to access the customer's online banking portal are applied in the PISP payment flow. Users can feel secure that they are fully in control and are not providing any sensitive details with a third party that is unknown to them. " %}

## AISP

When acting as an **AISP**, merchants can request clients to grant access to their account information via Open Banking.

For end users they:

* Select Open Banking Account Access on your merchant page.
* Select the bank where their account is held.
* Are redirected to this bank's online banking service.
* Verify themselves by providing their online banking credentials (as they would normally do when logging on to their online banking system).
* Select an account to share and confirm their consent to allow the merchant to access the account details, balance and/or transaction information.

{% include note.html content="Currently Nuapay functions in AISP mode in the [AIS E-Mandates flow](em_obaslaunching.html) and in the [User Verification](ver_landing_page.html) products." %}
