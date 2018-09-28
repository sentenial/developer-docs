---
title: Revoke all Direct Debits
keywords: Revoke all Direct Debits
summary: "Revoke all Direct Debits RESTful API"
sidebar: np_sidebar
permalink: np_revokealldds.html
folder: prodNuapay
toc: false
---

## API Details

As detailed in the <a href="np_revokedirectdebit.html">Revoke Direct Debit</a> section, it is possible to revoke a single Direct Debit payment that is in READY FOR EXPORT status. The Revoke All Direct Debits request allows you to revoke a number of payments, linked to a specific mandate, in a single request (for a fixed-length schedule).

{% include important.html content="Note that in a fixed-length schedule (e.g. 12 payments, €10 per Direct Debit) all payments are created in READY FOR EXPORT status when you create the payment schedule. When you use the Revoke All Direct Debits request, all these payments are revoked. In an open-ended schedule only one payment is created in READY FOR EXPORT at any point in time; when one payment is exported a new payment is created in READY FOR EXPORT status. When you use Revoke All against an open-ended schedule, only one payment is revoked and a new payment will be create in READY FOR EXPORT." %}


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
<td markdown="span">The Revoke All request will only revoke payments in READY FOR EXPORT status. This request should be used where a fixed-length schedule is linked to the mandate</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates/{MANDATE_ID}/revokealldirectdebits
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 OK</b> response code</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include httpcodes.html %}
    
 
    </div>


</div>

{% include swaggerlink.html %}

{% include links.html %}
