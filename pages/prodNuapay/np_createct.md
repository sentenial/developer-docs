---
title: Create Credit Transfer
keywords: Create Credit Transfer
summary: "Create Credit Transfer RESTful API"
sidebar: np_sidebar
permalink: np_createdct.html
folder: prodNuapay
toc: false
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %} 

Before you can generate a Credit Transfer (CT) payment, using this API request, you must have first <a href = "np_createbeneficiary.html">created a beneficiary</a>.

CT payments, unlike Direct Debit payments, do not require that the transaction is passed to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing system</a> days in advance of the collection date.

If you create your CT payment early enough on a specific working day, the funds could be credited to your beneficiary on the same day. If you create the payment later in the day then the CT will generally be credited to the beneficiary on the following business day.


{% include note.html content="If you have 2 or more Nuapay accounts configured and want to transfer funds between these accounts you will need to use the [Transfer Between Accounts](np_accounttransfer.html) service" %}


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
<td markdown="span">You must have created and reference a beneficiary (its resource ID) in your request</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/beneficiaries/{BENEFICIARY_ID}/credittransfers
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

<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#create-credit-transfer" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->


{% include links.html %}
