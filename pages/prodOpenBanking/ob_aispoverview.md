---
title: AISP Overview
keywords: Open Banking AISP Overview
summary: "Account Initiation Service Provider mode"
sidebar: ob_sidebar
permalink: ob_aispoverview.html
folder: prodOpenBanking
---

In Account Information Service Provider mode Nuapay allows you to access your clients' bank account data. 

{% include warning.html content="Users are in complete control of their accounts at all times and granting you access to their data must be strictly controlled. Users should be fully informed of their rights and know that they can cancel your access to their data at any time. We also strongly recommend that you are fully aware of your obligations under the General Data Protection Regulation (GDPR) when working with your clients' banking data. " %}

Account access can allow a merchant to retrieve the following data related to its clients' accounts:

* Account Balances
* Beneficiary Details
* Direct Debits
* Standing Orders
* Transaction details for:
  - Debits
  - Credits
  - General Details

Before querying any of these specific account details you must first generate a [Create Account Access](ob_createaccountaccess.html) request. 











