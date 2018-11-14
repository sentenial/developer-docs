---
title: List Credit Transfers
keywords: List Credit Transfers API
summary: "List Credit Transfers RESTful API"
sidebar: np_sidebar
permalink: np_listcts.html
folder: prodNuapay
toc: false
---

## API Details

The List Credit Transfers request allows you to view a collection of Credit Transfers linked to a:

* Single beneficiary
* All beneficiaries

Use an appropriate URI (as described below) to return the required collection of CTs.

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
<td markdown="span">You can return all CTs or filter based on beneficiary</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/beneficiaries/{BENEFICIARY_ID}/credittransfers
</td>
</tr>
<tr>
<td markdown="span">URI (Option 2)</td>
<td markdown="span">/credittransfers
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


<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#list-credit-transfers-get" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->


{% include links.html %}
