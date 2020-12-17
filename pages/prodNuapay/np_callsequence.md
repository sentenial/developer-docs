---
title: API Call Sequence
keywords: API Call Sequence
summary: "APIs must be called in a logical order: you must have a Creditor Scheme ID (in SEPA) or a Service User Number (in Bacs) before you create a mandate/DDI. You cannot create a payment without first creating a mandate/DDI. "
sidebar: np_sidebar
permalink: np_callsequence.html
folder: prodNuapay
---

When working with the Nuapay API you need to be aware that the sequence of requests is important. 

* You cannot create a Direct Debit payment without first having created a mandate/DDI with which to link it. 
* You cannot create a mandate/DDI without first having been assigned a Creditor Scheme ID (in SEPA) or a Service User Number (in Bacs). 
* A Nuapay merchant account must also be linked to the scheme. 

<img src="images/scheme_to_payment.png">

A signed mandate/DDI, which is in `ACTIVE` status (see [Mandate Statuses](np_mandatestatuses.html) for more on statuses), can be used to collect one or multiple Direct Debit transactions.

The following gives you a high-level view of the required stages:

1. Before you can create mandates you must have a `Creditor Scheme Identifier` and a Nuapay-issued `Merchant account`. Nuapay Support will provide you with these details for both the Sandbox and Production environments. 
1. With your Nuapay account and Payment Scheme configured (this may be a Bacs or a SEPA scheme) you can begin to add new mandates/DDIs.
1. Mandates/DDIs have specific statuses (a `PENDING` status, prior to signature for example). Your mandates/DDIs must be in `ACTIVE` status before you can collect payments.
1. Payment requests must be created a number of days prior to the desired collection date. In general payments may be created 2 business days before the desired <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.collection_date}}">collection date</a>.
1. As payments can fail for various reasons (insufficient funds in your payer's account or a disputed transaction, for example) from the time when the payment is first created up to a number of weeks after the payment, it is important to ensure that you account for any failed payments and design how your solution will handle these.

{% include links.html %}

## Integration Models

Nuapay allows for two integration methods:

|**Merchant**|With this approach, you access the required API services for your business; you are acting as a single entity.|
|**Partner**|In this model you are acting on behalf of merchants, which exist under your partner-level entity. The partner needs to retrieve an OAuth tokens, which represents a specific "child" merchant, and then call the required APIs on behalf of that merchant, using that token.|

For more on the the `Merchant` and `Partner` integrations, see the [Integration Overview](np_integrationoverview.html) section.