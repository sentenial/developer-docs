---
title: List Failed Direct Debits
keywords: List Failed Direct Debits API
summary: "List Failed Direct Debits RESTful API"
sidebar: np_sidebar
permalink: np_listfaileddds.html
folder: prodNuapay
toc: false
---

## API Details

Direct Debit payments can fail at various stages in their lifecycle.

Where you are creating payments via the API you will be informed in your API response when there is an error in your request. 

The List Failed Direct Debits API allows you to query any Bank-related rejects. It also allows you to list any Technical Rejects that you may have had (you will only have Technical Rejects if you are importing payments via file upload; API requests do not result in Technical Rejects).

Failed payments can be grouped into three basic types:

| Type | Description |
|-------|--------|
|Technical Rejects | If you are importing payments into Nuapay via a file upload, some payments may be rejected for failing business validation rules. You may receive a DD001 code, for example, if you reference a mandate that does not exist. Note that there are no Technical Rejects for API or UI-based payments. In the case of an API request the response will indicate in real time that the payment has failed (if you have provided an incorrect mandate reference in your Create Direct Debit call, for example, you will receive a 7021 error code). |
| Pre-settlement Failures | Payments that are created and exported that the Payer's bank then rejects or refuses before the settlement date.|
| Post-settlement Failures	 | Payments that are exported and accepted but the bank then fails after the settlement date. |

## API Details

The List Failed Direct Debits request allows you to return a list of all technical reject, pre-, and post-settlement failed payments. Note that you should schedule to run this request at various times in the lifecycle of your Direct Debits to ensure that you have the current statuses of your payments before and after the settlement date. Alternatively you could implement a Webhook for this.


{% include note.html content="Optionally you can use the technicalrejects boolean in your request. If technicalrejects is true then all Bank rejects and all technical rejects are returned; if set to false then only Bank rejects are returned." %}


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
<td markdown="span">Use the date filters to retrieve the required failed payment details</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/faileddirectdebits
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span">rejectcreatefrom, rejectcreateto
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
