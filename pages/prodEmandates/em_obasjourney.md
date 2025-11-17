---
title: The User Journey
keywords: Open Banking & E-Mandate PSU Flow
summary: "The PSU experience when opting to set up a subscription with Direct Debit as the payment method for future collections."
sidebar: em_sidebar
permalink: em_obasjourney.html
folder: prodEmandates
published: false
---

For Merchants/Partners who are using either the `CHECKOUT` or `REDIRECT` integration approach to set up a subscription, the following gives a summary of the user's interaction.

## The User Experience

{% include tip.html content="The following screens are taken from the Bacs Direct Debit (GBP) signup process; the SEPA flow has a similar set of steps." %}

To use the service (for Bacs in GBP currency), the user:

1. Click the **Setup Subscription** button on the merchant’s payment page (in `CHECKOUT` or `REDIRECT` mode):
<img src = "images/obem_acc_overview.png">
1. The user clicks **Continue** and is prompted to select a bank:
<img src = "images/obem_acc_selectBnk.png">
1. The user is redirected to the selected bank, logs on, gives consent to the account access request, selects an account and is redirected back to Nuapay to the mandate (<a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.ddi}}">DDI</a>) signup screen:
<img src = "images/obem_acc_mandSignup.png">
1. Note that the Account Holder Name, Sort Code and Account Number are pre-populated.
1. The user selects the check box to confirm account ownership, and that he/she is the sole signatory on the account, and clicks **Sign**. A Confirmation screen is displayed:

   <img src = "images/obem_acc_confirm.png">

Once the mandate/<a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.ddi}}">DDI</a> is signed, you can set up a schedule of payments for the subscription. See the [Direct Debit Overview](np_ddoverview.html) section for more information on how Direct Debit payments work.
