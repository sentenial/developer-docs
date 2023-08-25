---
title: Implementation Options
keywords: Open Banking Account Access Implementation Options
summary: "Account Access implementation Options"
sidebar: ob_sidebar
permalink: ob_aisimplementations.html
folder: prodOpenBanking
---

Account Access may be implemented in one of the following ways:

1. SELF_HOSTED
1. SELF_HOSTED_CALLBACK


## Implementation Overview

The following summarises the options available to both merchants and partners (acting on behalf of merchants):

<table>
  <tbody>    
    <tr>
      <td>Self-Hosted</td>
      <td>In this implementation mode:
      <ul>
      <li>The user interface is handled by you for Bank Selection.</li>       
      <li>The signal that the <a href="#" data-toggle="tooltip" data-original-title="Payment Service User - the person using the payment service - the payer.">PSU</a> and <a href="#" data-toggle="tooltip" data-original-title="The Account Servicing Payment Service Provider: this is the Bank or Payment Institution">ASPSP</a> have finished interacting is sent via a <strong>POST</strong> to the URL defined in the <code class="language-plaintext highlighter-rouge">merchantPostAuthUrl</code> of the <code class="language-plaintext highlighter-rouge">/consents/</code> request.

       </li></ul></td>
    </tr>
    <tr>
      <td>Self-Hosted-Callback</td>
      <td>In this implementation mode:
      <ul>
      <li>You handle the user interface and you also manage the ASPSP OAuth Callback URL</li>
      <li>The signal that the PSU and ASPSP are finished interacting is sent via a <strong>POST</strong> to the URL defined in the <code class="language-plaintext highlighter-rouge">merchantPostAuthUrl</code> of the <code class="language-plaintext highlighter-rouge">/consents</code> request.</li>
      <li>The details of how to process this callback differs from the <em>SELF_HOSTED</em> flow. You need to process the OAUTH callback from the ASPSP directly, parse the information and send it back to the Nuapay TPP platform. </li>
      <li>This option is useful if you want to style your callback handler or have mobile apps handle the callbacks using mobile deeplinking. </li>      
      <li>In the context of mobile apps, <strong>Deep Linking</strong> consists of using a uniform resource identifier (URI) that is opened within a mobile app rather than simply launching a Web browser. </li></ul></td>
    </tr>

  </tbody>
</table>

<div markdown="span" class="alert alert-info" role="alert"><i class="fas fa-info-circle"></i>  For a good overview and introduction to <b>Mobile Deep Linking</b> see this [Wikipedia](https://en.wikipedia.org/wiki/Mobile_deep_linking){:target="_blank"} article</div>

<!--
Note that it is possible to interact with the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a> as a merchant or as a partner. For a high-level view of the endpoints you need to call, based on your integration, jump to [Quick Start for Partners](ob_quickstartpart.html) or  [Quick Start for Merchants](ob_quickstart.html).

If you think you know the implementation that best suits your needs, select from the options below to dive right in:

|**Mode**|**Implementation**|
|Partner|[Checkout](ob_checkoutoverview.html)|
||[Self-Hosted](ob_selfsetupoverview.html)|
||[Self-Hosted-Callback](ob_selfcallbacksetupoverview.html)|
||[Redirect](ob_redirectoverview.html)|
|Merchant|[Checkout](ob_checkoutoverviewmerch.html)|
||[Self-Hosted](ob_selfsetupoverviewmerch.html)|
||[Self-Hosted-Callback](ob_selfcallbackmerch.html)|
||[Redirect](ob_redirectoverviewmerch.html)|
-->

{% include links.html %}
