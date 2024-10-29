---
title: PISP Checkout Setup
keywords: Checkout Payment Page Setup Javascript Add Open Banking Payment Page
summary: "Adding Open Banking (Checkout mode) as a payment option to your Payment Page requires configuration as outlined below. In Self-Hosted mode you must develop your own user interface."
sidebar: ob_sidebar
permalink: ob_checkoutoverviewV2.html
folder: prodOpenBanking
toc: true
---

## Overview

{% include note.html content="Checkout is one of four Open Banking implementation approaches available. See [Implementation Options](ob_pispimplementation.html) for more on this." %}

Note that the approach and sequence of API calls varies for **Merchants** (who are accessing the services for themselves) and **Partners** who are accessing the service on behalf of their merchants.

{% include warning.html content="Both the CHECKOUT and REDIRECT modes allow you to use the Nuapay user interface but we recommend the REDIRECT method as it is the more reliable approach: not all mobile devices are compatible with CHECKOUT and your users may encounter issues when using this mode." %}

{% include tip.html content="Select the appropriate tab below to view the endpoints required and the sequence of calls:
" %}


<ul id="profileTabs" class="nav nav-tabs">
    <li class="active"><a href="#profile" data-toggle="tab">Merchant</a></li>
    <li><a href="#about" data-toggle="tab">Partner</a></li>

</ul>
  <div class="tab-content">
<div role="tabpanel" class="tab-pane active" id="profile">

<!--Merchant -->

A detailed overview of the various steps involved in the <strong>Checkout</strong> flow is provided in the image below for <em>Merchants</em>.

{% include tip.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}


{% include image.html file="ob_checkout_flow-merchant.png" url="images/ob_checkout_flow-merchant.png" target = "_new" alt="Checkout Flow - Merchant" caption="CHECKOUT Flow - Merchant" %}
In <strong>Checkout</strong> mode you will:


<ol>
    <li>(Optionally) Use your API key to retrieve a merchant access token. (For more on this see <a href="ob_partnerintegration.html#api-details---post-tokens">retrieving tokens</a>).</li>
    <li>Call the <code>/payments</code> endpoint, using the OAuth token retrieved in the previous step (or else use your API Key) (see <a href="ob_createpayment.html">Create Payment</a>) and set the <code>integrationType</code> to <code>CHECKOUT</code>.</li>
    <li>Using the returned <code>userInterfacePaymentId</code> from step 2, call <strong>NuapayOpenbanking.showUI()</strong>, e.g., <code>NuapayOpenbanking.showUI('772d0ef5-596b-43de-a6a0-832c9ab7a7a5')</code> to display the bank selection screen to the user.</li>
    <li>The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank.</li>
    <li>The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.tpp}}">Nuapay TPP</a> will then redirect the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> to authorise the payment.</li>
    <li>Once finished at the bank, the user is redirected to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.tpp}}">Nuapay TPP</a>, where a payment summary screen is displayed.</li>
    <li>When the summary screen is closed (either when the user clicks <strong>Close</strong> or the pop-up self-closes after 30 seconds), a payment-finished event is passed to the parent window.</li>
</ol>

</div>

<div role="tabpanel" class="tab-pane" id="about">

<!--Partner.-->

A detailed overview of the various steps involved in the <strong>Checkout</strong> flow is provided in the image below for <em>Partners</em>.

{% include tip.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}

{% include image.html file="ob_checkout_flow.png" url="images/ob_checkout_flow-partner.png" target = "_new" alt="Checkout Flow - Partner" caption="CHECKOUT Flow - Partner" %}


In <strong>Checkout</strong> mode you will:


<ol>
    <li>Use your partner-level API key to retrieve a token representing the required merchant. (For more on this see <a href="ob_partnerintegration.html#api-details---get-organisations">list organisations</a> and <a href="ob_partnerintegration.html#api-details---post-tokens">retrieving tokens</a>).</li>
    <li>Call the <code>/payments</code> endpoint on behalf of the merchant, using the OAuth token retrieved in the previous step (see <a href="ob_createpayment.html">Create Payment</a>) and set the <code>integrationType</code> to <code>CHECKOUT</code>.</li>
    <li>Using the returned <code>userInterfacePaymentId</code> from step 2, call <strong>NuapayOpenbanking.showUI()</strong>, e.g., <code>NuapayOpenbanking.showUI('772d0ef5-596b-43de-a6a0-832c9ab7a7a5')</code> to display the bank selection screen to the user.</li>
    <li>The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank.</li>
    <li>The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.tpp}}">Nuapay TPP</a> will then redirect the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> to authorise the payment.</li>
    <li>Once finished at the bank, the user is redirected to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.tpp}}">Nuapay TPP</a>, where a payment summary screen is displayed.</li>
    <li>When the summary screen is closed (either when the user clicks <strong>Close</strong> or the pop-up self-closes after 30 seconds), a payment-finished event is passed to the parent window.</li>
</ol>


{% include tip.html content="Rather than redirect PSUs to the ASPSP on the desktop, you may offer a QR code on screen, which will allow users to use their mobile devices to complete the bank sign-in and payment autorisation. Because users complete the payment on a mobile devive, they can take advantage of biometric authentication, for example. For more on this see [QR Code Functionality](#qr-code-functionality) below. " %}


</div>
</div>

{% include checkout_steps.html %} <!--pulls in common steps for Partner and Merchant-->
