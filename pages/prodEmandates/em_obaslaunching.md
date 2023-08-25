---
title: Launching the Account Access & E-Mandate Setup Flow
keywords: Launching The Account Access & E-Mandate Setup Flow
summary: "Depending on the integration type you have implemented, the method for launching the Account Access & E-Mandate flow varies."
sidebar: em_sidebar
permalink: em_obaslaunching.html
folder: prodEmandates
---

{% include tip.html content="Before you can set up a subscription payment solution you must first be configured for Direct Debit processing. Read more about [Direct Debit Basics](np_mdtbasics.html) and discuss your requirements with your Account Manager, who can guide you on how best to configure Direct Debits for your specific business needs." %}

In order to launch the Open Banking Account Access and E-Mandate signup flow, the merchant needs:

* An E-Mandate token (the `token` returned in the Prepare E-Mandate (`POST /emandates`) request).
* Some JavaScript and CSS as described below.

## CHECKOUT Mode

To launch the flow In CHECKOUT mode:

* Call the [Prepare E-Mandate](em_prepare.html) endpoint to retrieve an e-mandate `token`.
* Apply CSS and JS file references to your payment page.
* Add a **Setup Subscription** button, which calls the `aisEmandates()` function.

## Calling the Prepare E-Mandate Endpoint

To generate an E-Mandate token:

1. Generate a server-to-server call to `/emandates`.
1. Ensure that you have referenced your API Key or OAuth token in the request.
1. The ``/emandates`` service is described in <a href="em_prepare.html">Prepare E-Mandate</a>.
1. Store the `token` returned in the response.


## Adding the CSS and JS File References

On your subscription setup page you will need to add the following:

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

## Adding The Set Up Subscription Button

At this point you have:

* Retrieved an e-mandate `token` (via the [Prepare E-Mandate](em_prepare.html) service).
* Added the JS and CSS references to your payment page.


To enable the <span class="label label-info">SET UP SUBSCRIPTION</span> button you will need to add an ``onclick`` event:

````
<a class="btn-primary" onclick="aisEmandates()">SET UP SUBSCRIPTION</a>

````

This onclick event triggers the following JavaScript, which launches the subscription signup pop-up:

````
NuapayOpenBanking.showEmandateAisp( /*[[${token}]]*/, /*[[${uiUrl}]]*/ );

````

Where:

* The `token` is the retrieved E-Mandate token.
* The `uiUrl` is = `https://api.nuapay.com/tpp-ui` (on Production)

Note that you will need to specify the correct URL based on whether you are testing or working in Production:

|SANDBOX|https://sandbox.nuapay.com/tpp-ui/|
|PRODUCTION| https://api.nuapay.com/tpp-ui/|


An example URL could be:

|https://api.nuapay.com/tpp-ui/app/emandate-ui/aisp?flow=JS_API&token=8084300c-1a5b-4c5c-8576-7712fd71b19a-bo8pw4qv6j|

{% include tip.html content="To avoid any issues with **pop-up blockers**, we recommend that you request your users to: <br/>
<br/>1. Click a button to choose to set up a subscription via Open Banking Account Access (allowing you to retrieve the E-Mandate token)
<br/>2. Click a second button to choose to start the flow (launching the pop-up with the `token` retrieved in step 1)
<br/><br/>Because launching the Overview screen in step 2 is a user-initiated action, your users will not be prompted to enable pop-ups.
" %}


## REDIRECT Mode

To launch the flow In REDIRECT mode:

* Call the [Prepare E-Mandate](em_prepare.html) endpoint to retrieve an e-mandate `token`.
* Construct the required URL to pass to the PSU as a subscription setup link.
* Use JavaScript, similar to the following:

````
NuapayOpenBanking.showEmandateAisp( "fe5d1946-2c57-45c9-865b-600016291081-bo43xegjom", "https:\/\/api.nuapay.com\/tpp-ui\/");
````
