---
title: Direct Debit Payments
keywords: Payments
summary: "Once your mandate is created you can link single Direct Debit or payment schedules to it."
sidebar: product2_sidebar
permalink: p2_sample2.html
folder: product2
---


## Direct Debit Payments

So what is a Direct Debit (DD) payment? 

Once you have a signed mandate from your payer you can begin to collect payments from the account specified in the mandate agreement.

All DD payments must have the following:

* A collection date (also referred to as a settlement date or due date)
* A payment amount
* (Optionally) an End-to-End Identifier
* (Optionally) Remittance Information

## The DD Transaction

The <b>Collection Date</b> (often referred to as the Settlement Date or Value Date)  must generally be set to 2 days in the future (this is to allow for payments to pass through Clearing). In some cases payments may need to have a later collection date but this is dependent on your specific SEPA scheme configuration.

The <b>payment amount</b> must be provided in Euros and cents.

An <b>End-to-End-Identifier</b> is a unique identification that is applied to all payments, which allows them to be tracked through their lifecycle (from initiation to collection to any potential future rejections). If you do not assign an end-to-end when creating a payment , Nuapay will automatically generate one for you.

<b>Remittance information</b> allows you to provide any additional information related to the payment.
{% include links.html %}
