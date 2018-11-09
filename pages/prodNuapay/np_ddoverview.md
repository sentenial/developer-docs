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

<p>The <b>collection date</b> must generally be set to 2 days in the future (this is to allow for payments to pass through <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">Clearing</a>). In some cases payments may need to have a later collection date but this is dependent on your specific SEPA scheme configuration.</p>

<p>The <b>payment amount</b> must be provided in Euros and cents.</p>

<p>An <b>End-to-End-Identifier</b> is a unique identification that is applied to all payments, which allows them to be tracked through their lifecycle (from initiation to collection to any potential future rejections). If you do not assign an end-to-end when creating a payment , Nuapay will automatically generate one for you.</p>

<p><b>Remittance information</b> allows you to provide any additional information related to the payment.</p>

## Prerequisites 

<p>Before you can set up any payments via the API please note that you must:</p>

* Reference an active mandate in your request.
* Have retrieved your Creditor Scheme ID resource (see <a href="np_listcredscheme.html">List Creditor Schemes</a> call in the API Basics section).


{% include links.html %}
