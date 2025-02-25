---
title: PISP Self-Hosted Setup
keywords: Redirect Payment Page Setup Javascript Add Open Banking Payment Page
summary: "Adding Open Banking (Self-Hosted mode) as a payment option to your Payment Page requires configuration as outlined below. In Self-Hosted mode you must develop your own user interface."
sidebar: ob_sidebar
permalink: ob_selfsetupoverview.html
folder: prodOpenBanking
toc: true
---

## Overview

{% include note.html content="Self-Hosted is one of four Open Banking implementation approaches available. See [Implementation Options](ob_pispimplementation.html) for more on this." %}

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

A detailed overview of the various steps involved in the <strong>SELF-HOSTED</strong> flow is provided for <em>Merchant</em> users in the image below.

{% include tip.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}

{% include image.html file="ob_selfhosted_flow-merchant.png" url="images/ob_selfhosted_flow-merchant.png" target = "_new" alt="Self-Hosted Flow" caption="SELF_HOSTED Merchant Flow" %}

To add Open Banking to your payment page you will need to carry out the following steps:

<ol>
  <li>(Optionally) Use your API key to retrieve a merchant access token. (For more on this, see <a href="ob_partnerintegration.html#api-details---post-tokens">retrieving tokens</a>).</li>
  <li>Call <code>GET /banks</code> to retrieve a list of all supported banks (see <a href="ob_getbank.html">Retrieve Banks</a>) to populate your Bank Selection screen. Where banks have specific branches (bank families), you will also need to call the <a href="ob_getbankfamilies.html">View Bank Families</a> endpoint. (See the section on Bank Families below for more information on this).</li>
  <li>Once the payer has selected a bank, call the <code>/payments</code> endpoint (see <a href="ob_createpayment.html">Create Payment</a>). Set the <code>integrationType</code> to <code>SELF_HOSTED</code>, specify the <code>bankId</code> provided by the payer, and set the <code>merchantPostAuthUrl</code> (this can be the partner or merchant URL). This will return the <code>aspspAuthUrl</code>, to which you can redirect your <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a>.</li>
  <li>Your payer interacts with the selected <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> to authorize the payment.</li>
  <li>The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a> posts the payment ID to the partner/merchant URL (<code>merchantPostAuthUrl</code>). See posting details below.</li>
  <li>Use <a href="ob_retrievepayment.html">Retrieve Payment</a> to determine the final payment status, if required (an optional step) or, alternatively, use Webhooks.</li>
</ol>



</div>

<div role="tabpanel" class="tab-pane" id="about">

<!--Partner.-->

A detailed overview of the various steps involved in the <strong>SELF-HOSTED</strong> flow is provided in the image below for <em>Partner</em> users:

{% include tip.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}

{% include image.html file="ob_selfhosted_flow-partner.png" url="images/ob_selfhosted_flow-partner.png" target = "_new" alt="Self-Hosted Flow" caption="SELF_HOSTED Partner Flow" %}


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
  {% include self_hosted_shared.html %}

## QR Code Solution

QR codes are a great way to initiate an Open Banking payment, via the `SELF-HOSTED` implementation option.

* Incorporating QR code-based payment initiation in your Open Banking application can unlock seamless and secure payment experiences for both in-store and online purchases.
* The generated QR code can be provided to a user on a Web site, in an email, or at a physical point-of-sale terminal, for example.
* By scanning a QR code, users are guided through a streamlined flow, selecting their bank and authorizing the transaction directly. 
* This approach enhances user convenience and minimizes manual entry errors, making it especially valuable for businesses aiming to improve checkout speed, reduce cart abandonment, or simplify bill payment processes.

<img src = 'images/qr_code_steps.png'>


The following describes the steps:

**Generate the QR Code**:

* The QR code will contain a URL pointing to your application's backend service, which will initiate the payment process.
* This URL should include a unique identifier (e.g., a payment request ID) that your backend can use to retrieve the necessary payment details.

**Backend Logic (`POST /payments` Endpoint)**:

* When the user scans the QR code, their device will access the URL and trigger a request to your backend service.
* Your backend should then utilize the `POST /payments` endpoint to create a new payment request with the Nuapay TPP API.
* The request body should include all essential payment details, such as the merchant ID, payment amount, currency, order details, and redirect URLs for success and failure scenarios.
* Crucially, the `integrationType` parameter should be set to `SELF_HOSTED` for this use case.
* The `bankId` parameter will be determined in the next step and included in this request.

**Bank Selection Screen**:
* Upon successful creation of the payment request, the `POST /payments` endpoint will return a response containing an `aspspAuthUrl`.
* This URL is the authorization URL for the chosen bank's online banking system.
* Your backend should redirect the user to this `aspspAuthUrl`.
* The user will then be presented with a list of banks on the screen.
* The user selects their bank, which determines the `bankId` value.

**User Authentication and Approval**:
* Once the user selects their bank, they are redirected to their bank's online banking system for authentication.
* After successful authentication, the user reviews the payment details and approves the transaction within their banking environment.

**Callback Handling (`POST /payments/callback` Endpoint)**:

* Following user authorization, the bank redirects the user back to the `merchantPostAuthUrl` provided in the initial `POST /payments` request.
* This URL should point to your backend service's callback endpoint.
* The bank will include parameters in this redirect, which your backend should forward to the `POST /payments/callback` endpoint.
* This endpoint handles the authorization response and provides a redirect URL to the appropriate page on your application, depending on the success or failure of the authorization.

**Payment Status Updates**:
* Your backend should periodically use the `GET /payments/{paymentId}` endpoint to check the status of the payment.
* Once the payment status transitions to `AUTHORISED` or another final state, your backend can update the order status in your system and provide feedback to the user.
