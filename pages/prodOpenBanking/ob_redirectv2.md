---
title: PISP Redirect Payment Page Setup
keywords: Redirect Payment Page Setup Javascript Add Open Banking Payment Page
summary: "Adding Open Banking (Redirect mode) as a payment option to your Payment Page requires a little configuration as outlined below. In Redirect mode you will use the Nuapay user interface for Bank Selection and Confirmation screens, with the screens being launched in a new browser window. Alternatively, you can use this mode if you would like to implement a setup where PSUs are emailed a link to the Bank Selection page or scan a QR code, for example."
sidebar: ob_sidebar
permalink: ob_redirectoverviewv2.html
folder: prodOpenBanking
---

{% include note.html content="Redirect is one of four implementation approaches available. See [Implementation Options](ob_pispimplementation.html) for more on this." %}

Note that the approach and sequence of API calls varies for **Merchants** (who are accessing the services for themselves) and **Partners** who are accessing the service on behalf of their merchants.

<!--TABS-->
<ul id="profileTabs" class="nav nav-tabs">
    <li class="merchant"><a href="#merchant" data-toggle="tab">Merchant</a></li>
    <li><a href="#partner" data-toggle="tab">Partner</a></li>

</ul>
<!--TABS-->

<div class="tab-content"> <!--Start of overall Panels -->
<div role="tabpanel" class="tab-pane merchant" id="merchant"> <!--Panel 1 Start-->

<h2>Merchant Overview</h2>
<p>A detailed overview of the various steps involved in the <strong>REDIRECT</strong> flow (for merchants) is provided in the image below.</p>

<div class="alert alert-info" role="alert">
    <strong>Tip:</strong> Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window.
</div>

<img src="images/ob_redirect_flow-merchant.png" alt="Redirect Flow - Merchant" target="_new">
<p class="caption">REDIRECT Flow - Merchant</p>

<p>In <strong>Redirect</strong> mode you will:</p>
<ol>
    <li>(Optionally) Use your API key to retrieve a merchant access token. (For more on this see <a href="tok_reqtokorg.html#request-an-access-token-for-an-organisation">Request Organisation Access Token</a>).</li>
    <li>Call the <code>/payments</code> endpoint (see <a href="ob_createpayment.html">Create Payment</a>), using the OAuth token retrieved in the previous step (or else use your API Key).</li>
    <li>Set the <code>integrationType</code> to <code>REDIRECT</code>. You must also provide the <code>merchantPostAuthUrl</code> - this is mandatory for the Redirect flow.</li>
    <li>The Nuapay TPP creates the payment object and returns the <code>userInterfacePaymentId</code>.</li>
    <li>The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> then needs to be redirected to the URI with the <code>userInterfacePaymentId</code>. You must build a URI that can be used on a web page or sent by an e-mail to the end user. The URL will be similar to the following (on the Production environment):
        <ul>
            <li><code>https://api.nuapay.com/tpp-ui/redirect?userInterfacePaymentId={userInterfacePaymentId}</code></li>
        </ul>
    </li>
    <li>The end user clicks the URI and the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a> (with the Bank selection window) is displayed in a new browser window.</li>
    <li>When the user selects a bank he/she is redirected to the selected <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> to authorise the payment.</li>
    <li>The ASPSP redirects the PSU back to the TPP UI which processes that callback.</li>
    <li>The TPP then redirects the PSU to the <code>merchantPostAuthUrl</code> with the parameters <code>userInterfacePaymentId</code>.</li>
    <li>Use <a href="ob_retrievepayment.html">Retrieve Payment</a> to determine the final payment status, if required (This integration also supports webhooks so you can be informed when the payment is completed).</li>
</ol>

<h3>Authorisation</h3>
<p>An API Key or an OAuth token uniquely identifies you on Nuapay and is required to allow you to use our API services.</p>
<p>For more on API Keys and OAuth, see the <a href="ob_generalrules.html">API Basics</a> section.</p>

<h3>Calling the Payment Endpoint</h3>
<p>The Open Banking payment endpoint returns a payment identifier on a successful invocation.</p>
<p>To generate a payment ID:</p>
<ol>
    <li>Generate a server-to-server call to <code>/payments</code>.</li>
    <li>Ensure that you have referenced your API Key or OAuth token in the request.</li>
    <li>The <code>/payments</code> service is described in <a href="ob_createpayment.html">Create Payment</a>.</li>
</ol>

<h3>Adding the CSS and JS File References</h3>
<p>On your payment page you will need to add the following:</p>

<p><strong>For Sandbox</strong></p>
<pre><code>&lt;script src="https://sandbox.nuapay.com/tpp-ui/js/nuapay-open-banking.js"&gt;&lt;/script&gt;</code></pre>

<p><strong>For Production</strong></p>
<pre><code>&lt;script src="https://api.nuapay.com/tpp-ui/js/nuapay-open-banking.js"&gt;&lt;/script&gt;</code></pre>

<h3>Adding The Open Banking Pay Button</h3>
<p>At this point you have:</p>
<ul>
    <li>Added the JS and CSS links to your payment page.</li>
    <li>Retrieved the payment ID (via the Create Payment service).</li>
</ul>

<p>To enable the <span class="label label-info">PAY</span> button you will need to add an <code>onclick</code> event. See the example below:</p>
<pre><code>&lt;a class="btn btn-primary" href="#" onclick="NuapayOpenBanking.redirect(uiid, tppUibaseUrl);"&gt;Pay Now&lt;/a&gt;</code></pre>
<p>This button will open the Select Banks on a new browser tab or window for the <code>userInterfacePaymentId</code> (the <code>uiid</code>).</p>

<h3>Reusing the Link</h3>
<p>If you have decided to email the link to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> or have provided a QR code, that user may begin the payment, drop out at some point without completing the payment and retry accessing the link later. In that case:</p>
<ul>
    <li>Where a link is accessed, the TPP will check the existing payment status in the TPP database.</li>
    <li>If the payment's current status means that the payment cannot proceed (e.g. if the payment is in <code>SETTLEMENT_REJECTED</code>) an alert is displayed to the user on the TPP and he/she cannot continue.</li>
    <li>If the payment is in status <code>PENDING</code> then the user will be able to proceed and complete the payment. Note that <code>PENDING</code> is the only status that will allow the PSU to proceed.</li>
</ul>

<div class="alert alert-info" role="alert">
    <strong>Note:</strong> If the PSU goes to the ASPSP and cancels, the <a href="ob_whpaymentdecl.html">Payment Declined Webhook</a> is triggered. However, if the PSU reuses that payment link later, the payment status will revert to <code>PENDING</code>, allowing the user to complete the payment, if required.
</div>

<!-- Start Panel2-->
<div role="tabpanel" class="tab-pane" id="partner">

<p>Partner Section</p>

</div> <!-- End Panel2-->
</div> <!--End of overall Panels -->



{% include links.html %}
