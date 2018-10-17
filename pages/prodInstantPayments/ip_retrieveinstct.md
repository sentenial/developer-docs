---
title: Retrieve Instant Payment
keywords: SEPA Instant CT Retrieve
summary: "Retrieve SCT Instant RESTful API"
sidebar: ip_sidebar
permalink: ip_retrieveinstct.html
folder: prodInstantPayments
toc: false
---


When an Instant Payment is created in the Origix IP system it is given a unique identifier (the URI). This identifier is returned in the response to the <a href ="ip_createinstct.html">Create Instant Payment</a> request.

The Retrieve Instant Payment request allows you to look up the details of a given payment. The payment's ID, end-to-end identifier, time stamp etc. are all returned.

You must provide the transaction's unique URI as a GET request:


## API Details


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
<td markdown="span">Requires the encoded ID of the payment resource,</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/instantpayments
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span"><b>instantPaymentId</b>
<br/><i>Encoded ID of the instant payment resource.</i>
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 OK</b> response code.</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
      {% include httpcodes.html %}
    
    
    </div>


</div>

{% include swaggerlink.html %}


{% include links.html %}
