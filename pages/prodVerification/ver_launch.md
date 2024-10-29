---
title: Launching the AIS Flow
keywords: Verification scoring
summary: "Once the account holder name is retrieved from the bank, a matching score is calculated."
sidebar: ver_sidebar
permalink: ver_launch.html
folder: prodNuapay
toc: false
---
## Overview

To initiate an AIS Verification check, you first need to generate a Verification ID:

1. Generate a server-to-server call to POST `/verifications`.
1. Decide in your request whether you want to open the flow as a pop-up (`CHECKOUT` mode) or as a new window/tab (`REDIRECT` mode): set this via `integrationType`.
1. Ensure that you have referenced your API Key or OAuth token in the request.
1. The `/verifications` service is described in [Create Verification](ver_reqverification.html).
1. In the response, you will need to store the `userInterfaceVerificationId`.


## Adding the CSS and JS File References

On the page where you are calling the Verification check, you will need to add the following:

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

## Adding the Verify Button

At this point you have:

* Added the JS and CSS links to your Verification Check page.
* Retrieved the `userInterfaceVerificationId` (via the [Create Verification](ver_reqverification.html) service).


To enable the <span class="label label-info">VERIFY</span> button you will need to add an ``onclick`` event. See the examples below:

For `CHECKOUT`:

````
<a class="btn btn-primary" href="#" onclick="NuapayOpenBanking.showVerificationUi('772d0ef5-596b-43de-a6a0-832c9ab7a7a5','https://sandbox.nuapay.com/tpp-ui/'');">Verify</a>

````
For `REDIRECT`

````
<a class="btn btn-primary" href="#" onclick="NuapayOpenBanking.redirectVerificationUi('772d0ef5-596b-43de-a6a0-832c9ab7a7a5', 'https://sandbox.nuapay.com/tpp-ui/'');">Verify</a>

````

|In the NuapayOpenBanking.showVerificationUi(**id**, url) and in the NuapayOpenBanking.redirectVerificationUi functions, the **id** is the `userInterfaceVerificationId`|

In this example, when the user clicks the **Verify** button:
* The Overview pop-up (or window/tab) for the identifier ``772d0ef5-596b-43de-a6a0-832c9ab7a7a5`` is displayed.
* The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> is directed to the Nuapay TPP (Sandbox) UI at ``https://sandbox.nuapay.com/tpp-ui/``.


Note that you will need to specify the correct URL based on whether you are testing on the Sandbox or working on Production:

|SANDBOX|https://sandbox.nuapay.com/tpp-ui/|
|PRODUCTION| https://api.nuapay.com/tpp-ui/|

{% include tip.html content="Always make sure the call to the JavaScript checkout flow pop-up is triggered via an `onclick` event.
Most browsers block pop-ups if they are called outside of user-triggered event handlers like `onclick`.
" %}


{% include links.html %}
