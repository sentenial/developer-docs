---
title: Cancel Payment Schedule
keywords: sample
summary: "Cancel Payment Schedule RESTful API"
sidebar: np_sidebar
permalink: np_cancelschedule.html
folder: prodNuapay
toc: false
---

## API Details

In a Fixed-Length schedule the <b>Cancel Payment Schedule</b> request will set the status of any READY FOR EXPORT Direct Debit transactions in a payment schedule to REVOKED.

In an open-ended schedule the current READY FOR EXPORT payment is updated to Cancelled and no additional payments will be added.

{% include important.html content="Direct Debits that have been EXPORTED are unaffected by the cancel payment schedule request" %}

(See <a href="np_ddstatuses.html">Direct Debit Statuses</a> for more information on the various payment statuses that are possible).

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
<td markdown="span">You must reference an active mandate with an active payment schedule</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates/{MANDATE_ID}/paymentschedules/{SCHEDULE_ID}/cancel
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

<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#cancel-schedule" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->

{% include links.html %}
