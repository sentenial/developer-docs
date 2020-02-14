---
title: Direct Debits Overview
keywords: Direct Debits Overview
summary: "Direct Debit payments allow you to pull payments from your customers' accounts, once you have your customers' authorisation via signed mandates."
sidebar: np_sidebar
permalink: np_ddoverview.html
folder: prodNuapay
---


## Direct Debit Elements

<p>Once you have a signed mandate from your payer you can begin to collect payments from the account specified in the mandate agreement.</p>

<p>All Direct Debit payments must have the following:</p>

* A collection date (also referred to as a settlement date or due date)
* A payment amount
* (Optionally) an End-to-End Identifier
* (Optionally) Remittance Information

|<b>Collection Date</b>     | The date funds will be transferred to your account; generally set to 2 days in the future (this is to allow for payments to pass through <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">EBA Clearing</a> or the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.bacs-clearing}}">Bacs Service</a>).|
|<b>Payment Amount</b>      | Provided in either EUR or GBP|
|<b>End-to-End-Identifier</b>       | a unique identification that is applied to all payments, which allows them to be tracked through their lifecycle (from initiation to collection to any potential future rejections). If you do not assign an end-to-end when creating a payment , Nuapay will automatically generate one for you.|
|<b>Remittance information</b>      | allows you to provide any additional information related to the payment.|


## Prerequisites 

<p>Before you can set up any payments via the API please note that you must:</p>

* Reference an active mandate in your request.
* Have retrieved your (encoded) Creditor Scheme ID / SUN resource identifier (see <a href="np_listcredscheme.html">List Creditor Schemes</a> call in the API Basics section).


{% include links.html %}