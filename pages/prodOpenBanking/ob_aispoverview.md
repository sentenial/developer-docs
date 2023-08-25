---
title: Account Information Service Overview
keywords: Open Banking AISP Overview
summary: "Account Initiation Service Provider mode"
sidebar: ob_sidebar
permalink: ob_aispoverview.html
folder: prodOpenBanking
---

Account Access via Open Banking allows <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.tpp}}">TPPs</a>, like Nuapay, to offer various services to allow merchants to interact with their clients' account information, once <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSUs</a> have provided their consent for the requested access.

Note that:

* Currently Nuapay only offers access to account information: the owner name and account details.
* Access to detailed transaction or balance information is not currently available.

## Nuapay Use Case

Currently Nuapay leverages the AIS APIs to offer an E-Mandate signup solution:
* Users provide consent to an account access request.
* Nuapay use this consent to retrieve the user's account details.
* This step allows merchants to confirm ownership of the account and also simplifies the signup process for the user (there is no need to key in an IBAN, for example).
* Once the user clicks *Sign* the mandate can be used to collect payments via Direct Debit.

For more on this, see the [Open Banking & E-Mandate Overview](em_oboverview.html) and the [Account Access & E-Mandate Setup](em_obaslaunching.html) section.
