---
title: List Payment Schedules
keywords: List Payment Schedules API
summary: "List Payment Schedules RESTful API"
sidebar: np_sidebar
permalink: np_listschedules.html
folder: prodNuapay
toc: false
---

## API Details

The List Payment Schedule request allows you to view a collection of payment schedules linked to:

* A Mandate
* A Specific Scheme
* All schemes (i.e. all schedules)

Use an appropriate URI (as described below) to return the required collection of Payment Schedules.

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
<td markdown="span">You can return all payment schedules or filter based on mandate or by scheme</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/paymentschedules
</td>
</tr>
<tr>
<td markdown="span">URI (Option 2)</td>
<td markdown="span">/schemes/{CS_ID}/mandates/{MANDATE_ID}/paymentschedules
</td>
</tr>
<tr>
<td markdown="span">URI (Option 3)</td>
<td markdown="span">/schemes/{CS_ID}/paymentschedules
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
