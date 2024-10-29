---
title: PISP Redirect Payment Page Setup
keywords: Redirect Payment Page Setup Javascript Add Open Banking Payment Page
summary: "Adding Open Banking (Redirect mode) as a payment option to your Payment Page requires a little configuration as outlined below. In Redirect mode you will use the Nuapay user interface for Bank Selection and Confirmation screens, with the screens being launched in a new browser window. Alternatively, you can use this mode if you would like to implement a setup where PSUs are emailed a link to the Bank Selection page or scan a QR code, for example."
sidebar: ob_sidebar
permalink: ob_redirectoverviewv3.html
folder: prodOpenBanking
toc: false
---

## Overview

{% include note.html content="Redirect is one of four Open Banking implementation approaches available. See [Implementation Options](ob_pispimplementation.html) for more on this." %}

Note that the approach and sequence of API calls varies for **Merchants** (who are accessing the services for themselves) and **Partners** who are accessing the service on behalf of their merchants.

{% include tip.html content="Select the appropriate tab below to view the endpoints required and the sequence of calls:
" %}


<ul id="profileTabs" class="nav nav-tabs">
    <li class="active"><a href="#profile" data-toggle="tab">Merchant</a></li>
    <li><a href="#about" data-toggle="tab">Partner</a></li>

</ul>
  <div class="tab-content">
<div role="tabpanel" class="tab-pane active" id="profile">

<!--Merchant -->

A detailed overview of the various steps involved in the <strong>REDIRECT</strong> flow is provided in the image below for <em>Merchant</em> users.

{% include tip.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}

{% include image.html file="ob_redirect_flow-merchant.png" url="images/ob_redirect_flow-merchant.png" target = "_new" alt="Redirect Flow - Merchant" caption="REDIRECT Flow - Merchant" %}

In <strong>Redirect</strong> mode you will:

<ol>
  <li>(Optionally) Use your API key to retrieve a merchant access token. (For more on this, see <a href="ob_partnerintegration.html#api-details---post-tokens">retrieving tokens</a>).</li>
  <li>Call the <code>/payments</code> endpoint (see <a href="ob_createpayment.html">Create Payment</a>), using the OAuth token retrieved in the previous step (or else use your API Key).</li>
  <li>Set the <code>integrationType</code> to <code>REDIRECT</code>. You must also provide the <code>merchantPostAuthUrl</code> - this is mandatory for the Redirect flow.</li>
  <li>The Nuapay TPP creates the payment object and returns the <code>userInterfacePaymentId</code>.</li>
  <li>The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> then needs to be redirected to the URI with the <code>userInterfacePaymentId</code>. You must build a URI that can be used on a web page or sent by an e-mail to the end user. The URL will be similar to the following (on the Production environment):
    <ul>
      <li><code>https://api.nuapay.com/tpp-ui/redirect?userInterfacePaymentId=&lt;userInterfacePaymentId&gt;</code></li>
    </ul>
  </li>
  <li>The end user clicks the URI, and the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a> (with the Bank selection window) is displayed in a new browser window.</li>
  <li>When the user selects a bank, he/she is redirected to the selected <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> to authorize the payment.</li>
  <li>The ASPSP redirects the PSU back to the TPP UI, which processes that callback.</li>
  <li>The TPP then redirects the PSU to the <code>merchantPostAuthUrl</code> with the parameters <code>userInterfacePaymentId</code>.</li>
  <li>Use <a href="ob_retrievepayment.html">Retrieve Payment</a> to determine the final payment status, if required. (This integration also supports webhooks so you can be informed when the payment is completed).</li>
</ol>

</div>

<div role="tabpanel" class="tab-pane" id="about">

<!--Partner.-->

A detailed overview of the various steps involved in the REDIRECT flow is provided in the image below for <em>Partner</em> users.

{% include tip.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}


{% include image.html file="ob_redirect_flow-partner.png" url="images/ob_redirect_flow-partner.png" target = "_new" alt="Redirect Flow - Partner" caption="REDIRECT Flow - Partner" %}


<ol>
  <li>Use your partner-level API key to retrieve a token representing the required merchant. (For more on this, see <a href="tok_listorgs.html">list organisations</a> and <a href="tok_reqtokorg.html">retrieving tokens</a>).</li>
  <li>Call the <code>/payments</code> endpoint (see <a href="ob_createpayment.html">Create Payment</a>), on behalf of the merchant, using the OAuth token retrieved in the previous step.</li>
  <li>Set the <code>integrationType</code> to <code>REDIRECT</code>. You must also provide the <code>merchantPostAuthUrl</code> - this is mandatory for the Redirect flow.</li>
  <li>The TPP creates the payment object and returns the <code>userInterfacePaymentId</code>.</li>
  <li>The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> then needs to be redirected to the URL with the <code>userInterfacePaymentId</code>. You must build a URI that can be used on a web page or sent by an email to the end user. The URL will be similar to the following (on the Production environment):
    <ul>
      <li><code>https://api.nuapay.com/tpp-ui/redirect?userInterfacePaymentId=&lt;userInterfacePaymentId&gt;</code></li>
    </ul>
  </li>
  <li>The end user clicks the link, and the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a> (with the Bank selection window) is displayed in a new browser window.</li>
  <li>When the user selects a bank, he/she is redirected to the selected <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> to authorize the payment.</li>
  <li>The ASPSP redirects the PSU back to the TPP UI, which processes that callback.</li>
  <li>The TPP UI then redirects the PSU to the <code>merchantPostAuthUrl</code> with the parameter <code>paymentId</code>.</li>
  <li>Use <a href="ob_retrievepayment.html">Retrieve Payment</a> to determine the final payment status. (This integration also supports webhooks so you can be informed when the payment is completed).</li>
</ol>



</div>
</div>

## Merchant Post-Auth URL Handling
The merchant merchantPostAuthUrl is sent as follows:

The payload of this request that you need to process includes:

**Headers** e.g. `Content-Type: application/x-www-form-urlencoded`
<br/>
**Body** e.g. `paymentId=4m6vjed32a&userInterfacePaymentId=95125314-5161-4769-926f-143ff6cbdd82`

Please note that the 'paymentId' allows you to look up the payment associated with this callback.


## Authorisation

An API Key or an OAuth token uniquely identifies you on Nuapay and is required to allow you to use our API services.

For more on API Keys and OAuth, see the <a href="ob_generalrules.html">API Basics</a> section.


## Calling the Payment Endpoint

The Open Banking payment endpoint returns a payment identifier on a successful invocation.

To generate a payment ID:

1. Generate a server-to-server call to `/payments`.
1. Ensure that you have referenced your API Key or OAuth token in the request.
1. The ``/payments`` service is described in <a href="ob_createpayment.html">Create Payment</a>.


## Adding the CSS and JS File References

On your payment page you will need to add the following:

**For Sandbox**

````
<script src="https://sandbox.nuapay.com/tpp-ui/js/nuapay-open-banking.js"></script>
````

**For Production**

````
<script src="https://api.nuapay.com/tpp-ui/js/nuapay-open-banking.js"></script>
````

## Adding The Open Banking Pay Button

At this point you have:

* Added the JS and CSS links to your payment page.
* Retrieved the payment ID (via the Create Payment service).

To enable the <span class="label label-info">PAY</span> button you will need to add an ``onclick`` event. See the example below:

````
<a class="btn btn-primary" href="#" onclick="NuapayOpenBanking.redirect(uiid, tppUibaseUrl);">Pay Now</a>

````

This button will open the Select Banks on a new browser tab or window for the `userInterfacePaymentId` (the `uiid`).

## Reusing the Link

If you have decided to email the link to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> or have provided a QR code, that user may begin the payment, drop out of the flow and retry accessing the link later. In that case:

* The TPP will check the existing payment status in the TPP database.
* If the payment's current status means that the payment cannot proceed (e.g. if the payment is in `SETTLEMENT_REJECTED`) an alert is displayed to the user on the TPP and he/she cannot continue.
* If the payment is in status `PENDING` then the user will be able to proceed and complete the payment. Note that `PENDING` is the only status that will allow the PSU to proceed.

{% include note.html content="If the PSU goes to the ASPSP and cancels, the [Payment Declined Webhook](ob_whpaymentdecl.html) is triggered. However if the PSU reuses that payment link later, the payment status will revert to `PENDING`, allowing the user to complete the payment, if required." %}


{% include links.html %}





{% include links.html %}
