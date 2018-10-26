---
title: E-Mandate Configuration
keywords: E-Mandate Configuration Config Emandate Setup
summary: "Various configurations and customisations are available when setting up your E-Mandates solution."
sidebar: em_sidebar
permalink: em_configuration.html
folder: prodEmandates
---


## API Information

Before you begin your implementation please ensure that you have:

* A valid *API Key*
* A *Creditor IBAN*
* The unique *Resource Identifier to the CSID*

When working with E-Mandate APIs note that all requests must:

* Be sent via the HTTPS protocol
* Pass a specific API Key unique to each merchant, for authentication
* Originate from an allowed IP address (the allowed IP addresses will be configured for you when you register for the service)
* Include (at a minimum) the mandatory fields required for the specific request that is being made


## Available End Points

Nuapay uses the JSON format to submit and retrieve data.

Note that in the API descriptions the endpoints use the LIVE URI.

We offer two separate endpoints for our E-Mandates API:

|LIVE| https://api.nuapay.com |
|Sandbox| https://sandbox.nuapay.com/ |


{% include note.html content="If you are a Java Developer please note that a Nuapay REST client is available on Github: [https://github.com/sentenial/nuapay-rest-client]( https://github.com/sentenial/nuapay-rest-client)" %}

## Configurations

{% include important.html content="Specific configurations must be carried out internally by Nuapay staff so please discuss your requirements with a member of our Customer Support team who will be able to assist you in this." %}

The following E-Mandate configurations may be customised for you as required:


|Email Alert|If turned on this setting will dispatch an email to notify you (the merchant) that a new e-mandate has been signed. This feature is particularly useful for smaller businesses with low volumes.|
|Logo| A custom logo can be displayed on the E-Mandate application - suitable for Redirect and Overlay implementations.|
|Third-Party Signing | A flag to indicate if additional third-party authorization is enabled. We partner with Morpho for mandates originating in France, for example, to provide an extra layer of archiving and traceability to protect your business against Refund claims. More suitable for larger businesses, please discuss your needs with our Customer Support team if you feel that this would be beneficial for your business.|
|User Interface Customizations| Various colour schemes are possible - please discuss your requirements with a member of the Customer Support team|
|White Labelling| Allowing you to hide the Sentenial or Nuapay branding.|
|Success and Failure URLs| Depending on the result of the create mandate operation, your customers will be redirected to either a Success page indicating that the mandate has been created or to a Failure page when there is an issue and a mandate is not generated. These URLs will be added as part of your configuration.|
|Display Extended Data|Depending on your business needs you may already have specific customer details (address details for example) and you may just want to collect your customer's IBAN. This setting allows you to just present a slimmed down set of input fields.|
|Debtor Input Allowed| This configuration is useful if you already have all of your customer's information; the E-Mandate application presents all the required data to the user - no input is required and the customer clicks Confirm to sign the mandate.|


{% include links.html %}
