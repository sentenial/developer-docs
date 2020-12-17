---
title: Direct Debits Overview
keywords: Direct Debits Overview
summary: "Direct Debit payments allow you to pull payments from your customers' accounts, once you have your customers' authorisation via signed mandates/DDIs."
sidebar: np_sidebar
permalink: np_ddoverview.html
folder: prodNuapay
---


## Direct Debit Elements

Once you have a signed mandate/DDI from your payer you can begin to collect payments from the account specified in the mandate/DDI agreement.

All Direct Debit payments must have the following:

* A <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.collection_date}}">Collection Date</a>.
* A payment amount
* (Optionally) an End-to-End Identifier
* (Optionally) Remittance Information

|**Collection Date**| The date funds will be transferred to your account; generally set to 2 days in the future (this is to allow for payments to pass through <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">EBA Clearing</a> or the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.bacs-clearing}}">Bacs Service</a>).|
|**Payment Amount**| Provided in either EUR or GBP|
|**End-to-End-Identifier**| A unique identification that is applied to all payments, which allows them to be tracked through their lifecycle (from initiation to collection to any potential future rejections). If you do not assign an end-to-end when creating a payment , Nuapay will automatically generate one for you.|
|**Remittance information**| Allows you to provide any additional information related to the payment.|


## Prerequisites 

Before you can set up any Direct Debit payments via the API please note that you must:

* Have retrieved your (encoded) Creditor Scheme ID / SUN resource identifier (see the [Creditor Schemes](np_listcredscheme.html) service). 
* Reference an **ACTIVE** mandate/DDI in your request. (See [Mandate/DDI Statuses](np_mandatestatuses.html) for more on the possible statuses.)

{% include links.html %}