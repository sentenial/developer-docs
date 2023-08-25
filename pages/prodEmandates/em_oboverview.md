---
title: Open Banking & E-Mandate Overview
keywords: Open Banking and E-Mandate setup
summary: "Combine Open Banking with an electronic mandate to better and more seamlessly manage subscription payments."
sidebar: em_sidebar
permalink: em_oboverview.html
folder: prodEmandates
---

{% include tip.html content="Open Banking allows third-party organizations (like Nuapay) to access banking transactions and data through APIs. For an added layer of security when signing up for Direct Debits, payers are required to connect to their bank (with Strong Customer Authentication) as an initial step in the signing process. For more information on Open Banking, see the [Open Banking section](ob_landing_page.html)" %}

Depending on your business requirements, you may generate an:

* Open Banking **Payment** with mandate/DDI signup.
  OR
* Open Banking **Account Access** request with mandate/DDI signup.

Nuapay Open Banking & E-Mandates support both the Bacs **Direct Debit scheme (GBP)** and also the **SEPA scheme (EUR)**.

Note that:

* To use the Nuapay User Interface, some client-side JavaScript is required to launch this flow.
* For `SELF-HOSTED` integrations, a Postman collection is available.

## Payment Initiation and E-Mandates

In the **Payment**-based flow:

1. The merchant creates a payment request initially (this might be a penny payment or it could be the first payment in a schedule).
1. The PSU selects a bank on the Nuapay User Interface.
1. He/she is redirected, logs on, and authorizes the payment at the selected bank.
1. The user is then passed back to Nuapay with the account details, which were used to make the payment, pre-filled on the Direct Debit signup page.
   Once the user reviews and confirms the mandate/DDI details, the merchant may arrange to collect future payments via Direct Debit.

   <img src="images/ob_emand_pisFlow.png">

## Account Access and E-Mandates

In the **Account-Access**-based flow, the user gives consent to use an account for the E-Mandate setup:

1. The user is prompted to select a bank.
1. Once redirected to the bank, the user logs on, and selects the bank account to use for the mandate/DDI setup.
1. The user is redirected back to Nuapay, to the Direct Debit Signup page, with the selected account's information pre-filled.
   Once the user confirms the mandate/DDI details, the merchant may then arrange to collect future payments via Direct Debit.   

   <img src="images/ob_emand_aisFlow.png">



## Benefits for Merchants

For **Merchants**:
Combining the Open Banking and Direct Debit signup is an attractive option because:

In the *Payment Flow*:
* Merchant can take a first payment and sign up the PSU for additional payments in one step.
* The PSU initially makes a payment through Open Banking; that first payment is collected immediately. As this is a bank transfer payment, there is no risk of a refund/chargeback.

In the *Payment Flow* and the *Account-Access* flow:

* The retrieved bank details are used to pre-populate the Electronic Mandate (E-Mandate) signup page, simplifying the signup for the PSU, meaning that drop-offs are reduced (PSUs do not need to manually type account details).
* Because account details have been retrieved from the user's bank (following the PSU completing Strong Customer Authentication at the bank) you can be confident that the payer is the account owner, massively reducing (if not fully eliminating) the fraud risk.
* Once the mandate/DDI is signed, future payments may be collected via Direct Debit, which is a pull payment method: merchants can set up a schedule and "pull" funds from their payers' accounts at regular intervals for subscription billing. The merchant is not relying on the payer to "push" payments.

## Benefits for Users

For **Users**:
* Setting up a bank transfer payment and Direct Debit payments is all handled in a single interaction with the merchant.
* Account details are automatically populated on the Direct Debit Signup screen so there is no need to find account details or to key them in.
* For EUR payments in particular, having to key in an IBAN can be tedious, which can result in drop offs.
* In the payment flow, as the first payment is made initially, the user can receive the merchant's service right away; there is no need to wait for a payment schedule to be created or a mandate/DDI to be activated.
* As in the standard Open Banking payment flow, users can scan a QR code to complete the flow on a mobile device, again simplifying the overall signup process.
