---
title: Cancel Mandate
keywords: sample
summary: "Cancel Mandate RESTful API"
sidebar: np_sidebar
permalink: np_cancelmandate.html
folder: prodNuapay
toc: false
---

## API Details

<p>When you cancel a mandate:</p>

* Any READY FOR EXPORT transactions linked to it are automatically cancelled.
* No further collections may be made against the mandate.

<p>If you want to engage with your payer at a later point and want to take direct debit payments, you will need to create a new mandate.</p>


{% include urls.html %}

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
<td markdown="span">Mandates must be in PENDING or SUSPENDED status</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates/{MANDATE_ID}/cancel
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 Created</b> response code</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include httpcodes.html %}
    
 
    </div>


</div>

<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#cancel-mandate" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->

{% include links.html %}
