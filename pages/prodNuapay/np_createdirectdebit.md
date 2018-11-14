---
title: Create Direct Debit
keywords: Create Direct Debit
summary: "Create Direct Debit RESTful API"
sidebar: np_sidebar
permalink: np_createdirectdebit.html
folder: prodNuapay
toc: false
---

## API Details

The Create Direct Debit request must:

* Include the resource identifier Creditor Scheme ID (CSID) (see the <a href="np_listcredscheme.html"> List Creditor Scheme</a> request)
* Reference an active mandate (its resource ID)

A successful request will result in a Direct Debit being set up in <b>READY_FOR_EXPORT</b> status: the payment is created but has not yet been forwarded to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">Clearing</a> for processing (see <a href ="np_ddstatuses.html">Direct Debit Statuses</a> for more information).

{% include tip.html content="Nuapay allows you to create a mandate and a Direct Debit payment in a single API request. For more details on this see the [Create Direct Debit and Mandate](np_createddandmand.html) request." %}



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

<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#create-direct-debit" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->

{% include links.html %}
