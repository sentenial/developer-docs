---
title: Re-present Failed Direct Debits
keywords: Re-present Failed Direct Debits
summary: "Re-present Failed Direct Debits RESTful API"
sidebar: np_sidebar
permalink: np_representfaileddds.html
folder: prodNuapay
toc: false
---

## API Details

Where a payment fails (for example for insufficient funds) you may want to re-try (or re-present) the payment.

The re-present request carries out two distinct steps:

* It updates the original failed payment's status to Re-presented
* It creates a new Direct Debit payment (with a new collection date and a new end-to-end ) in READY FOR EXPORT status

Optionally the new Direct Debit payment may also include a re-presentation fee


{% include note.html content="Certain SEPA Response codes will indicate that a re-presentation will be unsuccessful. For example an MD07 (debtor deceased) or an AC04 (Account closed). We recommend that you only attempt to re-present a failed payment for MS03 (Reason not specified) and AM04 (Insufficient funds)." %}


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
<td markdown="span">You can only re-present a failed Direct Debit payment (status REJECTED, RETURNED, etc.) Use when the original payment has failed with an MS03 or AM04.</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates/{MANDATE_ID}/directdebits/{DD_ID}/represent
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
