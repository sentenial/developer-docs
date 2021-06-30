---
title: The PSU Journey
keywords: Open Banking & E-Mandate PSU Flow
summary: "The PSU experience when opting to pay by Bank Transfer and set up Direct Debit as the payment method for future collections."
sidebar: ob_sidebar
permalink: ob_emoverallflow.html
folder: prodOpenBanking
---

For Merchants/Partners who are using either the `CHECKOUT` or `REDIRECT` integration approach, the following gives a summary of the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU's</a> interaction.

## The PSU's User Experience

To use the service, PSUs:

1. Click the **Pay** button on the merchant’s payment page (in CHECKOUT mode) or click a link (in REDIRECT mode) to launch the flow. Initially an overview page is displayed, giving an overview of the steps involved:
<img src = "images/obem_overview.png">
1. The user clicks **Continue** and is prompted to select a bank:
<img src = "images/obem_selectBnk.png">
1. The user is redirected to the selected bank, logs on and confirms the payment. Once redirected, the mandate (<a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.ddi}}">DDI</a>) signup screen is displayed:
<img src = "images/obem_mandSignup.png">
1. Note that the Account Holder Name, Sort Code and Account Number are pre-populated where:
  - The Account number was provided during the payment initiation (i.e. `debtorAccount` was provided in the [Create Payment](ob_createpayment.html) request).
  -	The Merchant has a Nuapay account and the payment transitions to `PAYMENT_RECEIVED` (see [Payment Statuses](ob_paymentstatuses.html) for more on the possible statuses).
  -	The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> returns the refund account information (only provided if the bank has implemented the OBIE 3.1.5 specification (or later)).
  -	(If any of the conditions above are not met then users are prompted to complete the form by manually keying in their account details).
1. The user selects the check box to confirm account ownership, and that he/she is the sole signatory on the account, and clicks **Sign**. A Confirmation screen is displayed:
<img src = "images/obem_confirm.png">


