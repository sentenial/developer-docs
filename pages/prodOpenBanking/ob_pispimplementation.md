---
title: PISP Implementation Options
keywords: Open Banking PISP Implementation Options
summary: "Payment Initiation Service Provider Checkout Page implementation Options"
sidebar: ob_sidebar
permalink: ob_pispimplementations.html
folder: prodOpenBanking
---

Your PISP checkout page may be implemented in one of the following ways:

1. CHECKOUT
1. SELF_HOSTED
1. SELF_HOSTED_CALLBACK

{% include warning.html content="SELF_HOSTED_CALLBACK mode is currently only available in the Nuapay Test environment." %}

The implementation you choose determines if you:

* Use the default Nuapay user interface or implement your own design.
* Choose the `merchantPostAuthUrl`; this is the URL that is used to signal to merchants/partners that the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> is finished interacting with the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>.
 

## What is the Callback URL?

To understand the Callback URL, and how it is used in Nuapay Open Banking, take the following "Happy" flow for an Open Banking payment... 

In an Open Banking payment the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a>:

1. Decides to pay via an account-to-account transfer (an Open Banking payment) and is presented with a list of banks from which to choose.
1. Selects the bank with which he/she holds an account.
1. Is re-directed to the selected bank's online banking system.
1. Logs on to the online banking system as normal and approves the payment.
1. Is automatically logged off from the online banking session (having approved the open banking payment) and is redirected back to the open banking eco system using the callback URL.

The implementation approach you take determines on which URL (defined in the callback) your payer finishes his/her Open Banking payment journey.

## Implementation Overview

The following summarises the options available to both merchants and partners (acting on behalf of merchants):

<table>
  <tbody>
    <tr>
      <td><strong>Implementation</strong></td>
      <td><strong>Details</strong></td>
    </tr>
    <tr>
      <td>Checkout</td>
      <td>In this implementation mode: 
      <ul>
      <li>You use the Nuapay user interface for the Bank Selection and you don’t set any <code class="language-plaintext highlighter-rouge">merchantPostAuth</code> URL in the request to <code class="language-plaintext highlighter-rouge">/tpp/payments</code>.</li> 
      <li>The signal that the <a href="#" data-toggle="tooltip" data-original-title="Payment Service User - the person using the payment service - the payer.">PSU</a> and <a href="#" data-toggle="tooltip" data-original-title="The Account Servicing Payment Service Provider: this is the Bank or Payment Institution">ASPSP</a> have finished interacting is sent via a JavaScript event to the Web page hosting the NuaPay Payment User Interface.</li> 
      <li>You will need to configure a <a href="ob_checkoutoverviewmerch.html#adding-a-listener">Listener</a> for this close event.</li></ul></td>
    </tr>
    <tr>
      <td>Self-Hosted</td>
      <td>In this implementation mode:
      <ul>
      <li>The user interface is handled by you for Bank Selection.</li>       
      <li>The signal that the <a href="#" data-toggle="tooltip" data-original-title="Payment Service User - the person using the payment service - the payer.">PSU</a> and <a href="#" data-toggle="tooltip" data-original-title="The Account Servicing Payment Service Provider: this is the Bank or Payment Institution">ASPSP</a> have finished interacting is sent via a <strong>POST</strong> to the URL defined in the <code class="language-plaintext highlighter-rouge">merchantPostAuthUrl</code> of the <code class="language-plaintext highlighter-rouge">/tpp/payment</code> request.
       For more on this see <a href= "ob_selfsetupoverview.html#merchantpostauthurl-handling">Processing the Callback</a>
       </li></ul></td>
    </tr>
    <tr>
      <td>Self-Hosted-Callback</td>
      <td>In this implementation mode: 
      <ul>
      <li>You handle the user interface and you also manage the ASPSP OAuth Callback URL</li> 
      <li>The signal that the PSU and ASPSP are finished interacting is sent via a <strong>POST</strong> to the URL defined in the <code class="language-plaintext highlighter-rouge">merchantPostAuthUrl</code> of the <code class="language-plaintext highlighter-rouge">/tpp/payment</code> request.</li>
      <li>The details of how to process this callback differs from the <em>SELF_HOSTED</em> flow. You need to process the OAUTH callback from the ASPSP directly, parse the information and send it back to the Nuapay TPP platform. For more on this see <a href= "ob_selfcallbacksetupoverview.html#processing-the-callback">Processing the Callback</a></li> 
      <li>This option is useful if you want to style your callback handler or have mobile apps handle the callbacks using mobile deeplinking. </li>      
      <li>In the context of mobile apps, <strong>Deep Linking</strong> consists of using a uniform resource identifier (URI) that is opened within a mobile app rather than simply launching a Web browser. </li></ul></td>
    </tr>
  </tbody>
</table>

<div markdown="span" class="alert alert-info" role="alert"><i class="fas fa-info-circle"></i>  For a good overview and introduction to <b>Mobile Deep Linking</b> see this [Wikipedia](https://en.wikipedia.org/wiki/Mobile_deep_linking){:target="_blank"} article</div>

Note that it is possible to interact with the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a> as a merchant or as a partner. For a high-level view of the endpoints you need to call, based on your integration, jump to [Quick Start for Partners](ob_quickstartpart.html) or  [Quick Start for Merchants](ob_quickstart.html).

If you think you know the implementation that best suits your needs, select from the options below to dive right in:

|**Mode**|**Implementation**|
|Partner|[Checkout](ob_checkoutoverview.html)|
||[Self-Hosted](ob_selfsetupoverview.html)|
||[Self-Hosted-Callback](ob_selfcallbacksetupoverview.html)|
|Merchant|[Checkout](ob_checkoutoverviewmerch.html)|
||[Self-Hosted](ob_selfsetupoverviewmerch.html)|
||[Self-Hosted-Callback](ob_selfcallbackmerch.html)|



{% include links.html %}
