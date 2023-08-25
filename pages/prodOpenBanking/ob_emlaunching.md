---
title: Launching the Payment & E-Mandate Setup Flow
keywords: Launching The Payment & E-Mandate Setup Flow
summary: "Depending on the integration type you have implemented, the method for launching the Open Banking & E-Mandate flow varies."
sidebar: ob_sidebar
permalink: ob_emlaunching.html
folder: prodOpenBanking
---

{% include tip.html content="Before you can set up a subscription payment solution you must first be configured for Direct Debit processing. Read more about [Direct Debit Basics](np_mdtbasics.html) and discuss your requirements with your Account Manager, who can guide you on how best to configure Direct Debits for your specific business needs." %}

In order to launch the Open Banking Payment and E-Mandate signup flow, the merchant needs:

* A User Interface Payment ID (the `userInterfacePaymentId` returned in the [Create Payment](ob_createpayment.html) request).
* A reference to the Direct Debit scheme to be used.
  * For GBP payments, a Bacs Service User Number - <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.sun}}">SUN</a> is required.
  * For EUR payments, the SEPA Scheme Identifier is required.
  * In both Bacs and SEPA, this identifier is passed in the `creditorSchemeIdentifier`. Call `GET /schemes` ([List Schemes](np_listcredscheme)) to retrieve your scheme identifier.

These elements are required for both the `CHECKOUT` and the `REDIRECT` integrations.

## CHECKOUT Mode

In CHECKOUT mode, in order to launch the Payment & E-Mandate flow, you will need to:

* Call the [Create Payment](ob_createpayment.html) endpoint to retrieve the `userInterfacePaymentId`.
* Apply CSS and JS file references to your payment page.
* Add a **Pay** button, which calls the `showPaymentUI` function.

## Calling the Create Payment Endpoint

The Open Banking payment endpoint returns a payment identifier on a successful invocation.

To generate a payment ID:

1. Generate a server-to-server call to `/payments`.
1. Ensure that you have referenced your API Key or OAuth token in the request.
1. The ``/payments`` service is described in <a href="ob_createpayment.html">Create Payment</a>.
1. In the response, you will need to store the `userInterfacePaymentId`.


## Adding the CSS and JS File References

On your payment page you will need to add the following:

**For Sandbox**

````
<script src="https://sandbox.nuapay.com/tpp-ui/js/nuapay-open-banking.js"></script>
<link rel="stylesheet" type="text/css" href="https://sandbox.nuapay.com/tpp-ui/css/nuapay-open-banking.css" />
````

**For Production**

````
<script src="https://api.nuapay.com/tpp-ui/js/nuapay-open-banking.js"></script>
<link rel="stylesheet" type="text/css" href="https://api.nuapay.com/tpp-ui/css/nuapay-open-banking.css" />
````

## Adding The Open Banking Pay Button

At this point you have:

* Retrieved the `userInterfacePaymentId` (via the [Create Payment](ob_createpayment.html) service).
* Added the JS and CSS references to your payment page.


To enable the <span class="label label-info">PAY</span> button you will need to add an ``onclick`` event. See the (GBP Bacs) example below:

````
<a class="btn btn-primary" href="#" onclick="NuapayOpenBanking.showPaymentUI('123456', 772d0ef5-596b-43de-a6a0-832c9ab7a7a5';'https://sandbox.nuapay.com/tpp-ui/’);">Pay Now</a>

````

The function takes three parameters:
1. The `creditorSchemeId` (i.e. the SUN; 123456 in the example above): this is the actual SUN and not its encoded value.
1. The `userInterfaceIdentifier` (772d0ef5-596b-43de-a6a0-832c9ab7a7a5 in the example above)
1. The `url` (https://sandbox.nuapay.com/tpp-ui/)

Note that you will need to specify the correct URL based on whether you are testing or working in Production:

|SANDBOX|https://sandbox.nuapay.com/tpp-ui/|
|PRODUCTION| https://api.nuapay.com/tpp-ui/|

{% include tip.html content="To avoid any issues with **pop-up blockers**, we recommend that you request your users to: <br/>
<br/>1. Click a button to pay by Open Banking (allowing you to retrieve the payment identifier)
<br/>2. Click a second button to choose to start the flow (launching the pop-up with the payment identifier retrieved in step 1)
<br/><br/>Because launching the Overview screen in step 2 is a user-initiated action, your users will not be prompted to enable pop-ups.
" %}


## REDIRECT Mode

To launch the Payment and E-Mandate flow In REDIRECT mode:

* Call the [Create Payment](ob_createpayment.html) endpoint to retrieve the `userInterfacePaymentId`.
* Construct the required URL to pass to the PSU as a payment link.

In the standard `REDIRECT` Open Banking payment, a URL similar to the following is used:

|/tpp-ui/redirect?userInterfacePaymentId=userInterfacePaymentId|

To launch the Payment and E-Mandate flow, the URL becomes:

|/tpp-ui/**paymentui**/redirect?**creditorSchemeId=SUN**&userInterfacePaymentId=userInterfacePaymentId|

Note that the URL:

* Includes /paymentui/
* The value of the SUN is the 6-digit identifier (not the encoded identifier).
