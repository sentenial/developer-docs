---
title: The User Journey
keywords: Open Banking & E-Mandate PSU Flow
summary: "The PSU experience when opting to pay by Bank Transfer and set up Direct Debit as the payment method for future collections."
sidebar: em_sidebar
permalink: em_obpsjourney.html
folder: prodEmandates
---

For Merchants/Partners who are using either the `CHECKOUT` or `REDIRECT` integration approach, the following gives a summary of the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU's</a> interaction.

## The User Experience

{% include tip.html content="The following screens are taken from the Bacs Direct Debit (GBP) signup process; the SEPA flow has a similar set of steps." %}

To use the service (for Bacs in GBP currency), PSUs:

1. Click the **Setup Subscription** button on the merchant’s payment page (in `CHECKOUT` or `REDIRECT` mode):
<img src = "images/obem_overview.png">
1. The user clicks **Continue** and is prompted to select a bank:
<img src = "images/obem_selectBnk.png">
1. The user is redirected to the selected bank, logs on, approves the payment and is redirected back to Nuapay to the mandate (<a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.ddi}}">DDI</a>) signup screen:
<img src = "images/obem_mandSignup.png">
1. Note that the Account Holder Name, Sort Code and Account Number are pre-populated where:
  - The Account number was provided during the payment initiation (i.e. `debtorAccount` was provided in the [Create Payment](ob_createpayment.html) request).
  -	The Merchant has a Nuapay account and the payment transitions to `PAYMENT_RECEIVED` (see [Payment Statuses](ob_paymentstatuses.html) for more on the possible statuses).
  -	The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> returns the refund account information (only provided if the bank has implemented the OBIE 3.1.5 specification (or later)).
  -	(If any of the conditions above are not met then users are prompted to complete the form by manually keying in their account details).
1. The user selects the check box to confirm account ownership, and that he/she is the sole signatory on the account, and clicks **Sign**. A Confirmation screen is displayed:
<img src = "images/obem_confirm.png">

Once the mandate/<a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.ddi}}">DDI</a> is signed, you can set up a schedule of payments for the subscription. See the [Direct Debit Overview](np_ddoverview.html) section for more information on how Direct Debit payments work.
