---
title: E-Mandate & Contract Overview
keywords: E-Mandate and Contract Overview
summary: "Electronically sign your mandate and a contract in a single operation."
sidebar: em_sidebar
permalink: em_contractoverview.html
folder: prodEmandates
---

## Background 

For a lot of businesses, seeking authorisation for Direct Debit payments is just one step when signing up a new customer; Merchants often require a signed contract too before offering their specific goods or services.

The E-Mandates solution allows you to leverage the power of our API to offer your customers the option to sign up for both a **Direct Debit Mandate** and also for a specific **contract** all in a single sign operation.

When you use this feature, users will see a screen similar to the following, with the customer being able to click the Terms and Conditions link to view the details of the contract prior to signing:

<img src="images/mand_contract.png">

Once signed, the contract and mandate are combined and stored as a single PDF document.

## Setup

To set up contract and mandate signing together:

* Use the <a href ="em_contractupload.html">POST/contracts</a> call to upload your PDF contract document to the E-Mandates application.
* Store the resource identifier of your contract document (returned in the response)
* Reference this identifier in the Prepare Mandate call (in one of the following Prepare E-Mandate calls, depending on your integration):
  - Redirect E-mandate Token
  - Overlay E-mandate Token
  - Direct API E-mandate Token


{% include note.html content="It is not possible to combine a contract and mandate if you are using the WordPres integration option." %}

{% include important.html content="If you use Third-Party Signing (see the [Configuration](em_configuration.html) section), the single PDF document (contract and mandate) are signed together." %}



{% include links.html %}
