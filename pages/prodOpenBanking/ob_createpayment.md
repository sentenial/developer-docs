---
title: Create Payment
keywords: Create Open Banking Payment
summary: "Create Open Banking Payment RESTful API"
sidebar: ob_sidebar
permalink: ob_createpayment.html
folder: prodOpenBanking
toc: false
---

## API Details

The Create Payment service generates an Open Banking payment object, returning a unique ``paymentId`` with an (initial) status of  ``PENDING_APPROVAL``.

{% include tip.html content="We recommend that you use a unique idempotency key with each unique Create Open Banking Payment request. The **x-idempotency-key** is a Header parameter in this API." %}



<ul id="profileTabs" class="nav nav-tabs">
    <li class="active"><a href="#profile" data-toggle="tab">Request</a></li>
    <li><a href="#about" data-toggle="tab">Response</a></li>
   
</ul>
  <div class="tab-content">
<div role="tabpanel" class="tab-pane active" id="profile">


  <table>
<colgroup>
<col width="30%" />
<col width="90%" />
</colgroup>

<tbody>
<tr>
<td markdown="span">Usage</td>
<td markdown="span">This POST request will return a unique payment identifier. This will be used later to render the Bank selection screen to end users on the UI.</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/payments
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span"><b>amount</b>
<br/><i>The amount</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>currency</b>
<br/><i>The ISO currency code.</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>reference</b>
<br/><i>The merchant reference for this payment; this can be used later to link the Nuapay reference to the internal merchant reference.</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>countryCode</b> 
<br/><i>The ISO country code of the payer.</i>
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>201 Created</b> response code</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include ob_httpcodes.html %}
    
 
    </div>


</div>

{% include ob_swaggerlink.html %}

{% include links.html %}
