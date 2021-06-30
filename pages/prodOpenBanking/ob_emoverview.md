---
title: Open Banking & E-Mandate Overview
keywords: Open Banking Payment and E-Mandate setup
summary: "Combine an Open Banking tranfer payment with an electronic mandate to better and more seamlessly manage subscriptions."
sidebar: ob_sidebar
permalink: ob_emoverview.html
folder: prodOpenBanking
---

Merchants and Partners may combine an Open Banking payment with an electronic mandate (Direct Debit Instruction – DDI) signup. This means that a merchant can take an initial bank transfer payment and then use the same payer account details to automatically create a Direct Debit mandate to collect subsequent payments.

Note that:

* For CHECKOUT and REDIRECT integrations, some client-side JavaScript is required to launch this flow.
* For SELF-HOSTED integrations, a Postman collection is provided.
* Only GBP bank transfer payments are currently supported; the signup process is only for Bacs Direct Debit. 


## Benefits for Merchants

For **Merchants**:
Combining the Open Banking payment and the DDI signup is an attractive option because:

* They can take a first payment and sign up the PSU for additional payments in one go. 
* The PSU initially makes a payment through Open Banking; that first payment is collected immediately. As this is a bank transfer payment, there is no risk of a refund/chargeback.
* The bank details provided for the Bank Transfer payment are used to pre-populate the E-Mandate signup page, simplifying the signup for the PSU meaning that drop-offs are reduced (PSUs do not need to manually type account details). 
* Because account details have been retrieved from the payer’s bank (following the PSU completing Strong Customer Authentication at the bank) you can be confident that the payer is the account owner, massively reducing (if not fully eliminating) the fraud risk.

## Benefits for PSUs

For **PSUs**:
* Setting up a bank transfer payment and Direct Debit payments is all handled in a single interaction with the merchant.
* Account details are automatically populated on the Direct Debit Signup screen so there is no need to find account details or to key them in.
* As in the standard Open Banking payment flow, users can scan a QR code to complete the payment flow on a mobile device, again simplifying the overall signup process.


