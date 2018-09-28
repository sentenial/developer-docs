---
title: API Call Sequence
keywords: API Call Sequence
summary: "APIs must be called in a logical order: you must have a Creidtor Scheme ID before you create a mandate. You cannot create a payment without first creating a mandate. "
sidebar: np_sidebar
permalink: np_callsequence.html
folder: prodNuapay
---

<p>When working with the Nuapay API you need to be aware that the sequence of requests is important. You cannot create a payment without first having created a mandate; you cannot create a mandate without first having a Creditor Scheme ID.</p>

<p>The following gives you a high-level view of the required stages:</p>

1. Before you can create mandates you must have a Creditor Scheme Identifier and a Merchant account. You will need to provide your account details to the Nuapay Support team when you are registering .

1. The Nuapay Support team will create a Nuapay virtual account (IBAN). This account will link to your physical IBAN. The support team will also create a Creditor Scheme ID for you. These details will be shared with you.
1. With your Nuapay account and Payment Scheme configured (this will generally be a SEPA CORE scheme) you can begin to add new mandates.
1. Mandates have specific statuses (a Pending status, prior to signature; Active once signed). Your mandates must be in Active status before you can collect payments.
1. Payment requests must be created a number of days prior to the desired collection date - this is a requirement of the SEPA scheme. In general payments may be created 2 business days before the desired collection date.
1. As payments can fail for various reasons (insufficient funds in your payer's account or a disputed transaction, for example) from the time when the payment is first created up to a number of weeks after the payment, it is important to ensure that you account for any failed payments and design how your solution will handle these.

{% include links.html %}
