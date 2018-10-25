---
title: Reverse Payment
keywords: Reverse Open Banking Payment
summary: "Reverse an Open Banking Payment RESTful API"
sidebar: ob_sidebar
permalink: ob_reversepayment.html
folder: prodOpenBanking
toc: false
---

## API Details

The Reverse Payment service allows you to reverse/refund an Open Banking payment. 

{% include important.html content="Reversing a payment is only possible if you are using a Nuapay account as your merchant account; if your Open Banking payments have not been credited to this account then the Nuapay system has no beneficiary account reference and cannot reverse the funds to the appropriate customer account. " %}

A successful request will put the payment into REVERSE_REQUESTED status. The payment will be automatically debited from your Nuapay account and credited to your customer's account. 

Once the payment is successfully refunded (with funds disbursed to your customer's account) a Webhook notification will be fired to your configured Webhooks Endpoint. See <a href="ob_whrreversed.html">Payment Reversed</a> in the Webhooks section for more details.

{% include note.html content="Depending on the payment scheme you are using reversed payments may be settled the following business day e.g. for SEPA CTs or funds may be credited in a matter of seconds via the SEPA CT Instant Scheme or via Faster Payments in the UK." %}


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
<td markdown="span">You must pass the paymentId.</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/payments/{paymentId}/reverse
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 resource retrieved</b> response code, including details of the payment - status, amount, currency etc.</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include ob_httpcodes.html %}
    
 
    </div>


</div>

{% include swaggerlink.html %}

{% include links.html %}
