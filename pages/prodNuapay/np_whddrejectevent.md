---
title: Direct Debit R-Transaction Event
keywords: Direct Debit R-Transaction Event Webhook 
summary: "Direct Debit R-Transaction Webhook event"
sidebar: np_sidebar
permalink: np_whddrejectevent.html
folder: prodNuapay
toc: false
---
 
{% include webhook.html content="A PAIN.002 reject file is imported into Nuapay updating a Direct Debit's [payment status](np_ddstatuses.html)." %}


{% highlight json linenos  %}
POST http://example.com/webhooks
Content-Type: application/json;charset=UTF-8
X-Signature: 521ab01d030dee864fb44cc65a3be52ae591f46cde8d14d3e72fbc3790e4a304
Content-Length: 261
X-Request-Id: dc645679-71a5-498d-bb29-ec027948c7c1
	{
		"eventTimestamp": 1501169079000,
		"eventType": "DirectDebitReject",
		"resourceReference": "Webhook1",
		"resourceReferenceType": "EndToEndId",
		"resourceUri": "/schemes/p2lqa394mv/mandates/lbyjxj5ebd/directdebits/a2rexnvdmq",
		"resourceType": "DirectDebit",
		"reasonCode": "MS03"
	}
{% endhighlight %}





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
<td markdown="span">You must reference an ACTIVE mandate</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates/{MANDATE_ID}/directdebits
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span">requestedCollectionDate, paymentAmount
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>201 Created</b> response code</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include httpcodes.html %}
    
 
    </div>


</div>

{% include swaggerlink.html %}

{% include links.html %}
