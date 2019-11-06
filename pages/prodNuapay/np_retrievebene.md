---
title: Retrieve Beneficiary
keywords: Retrieve Beneficiary API
summary: "Retrieve Beneficiary RESTful API"
sidebar: np_sidebar
permalink: np_retrievebene.html
folder: prodNuapay
toc: false
---

## API Details

The Retrieve Beneficiary returns the details of a specific beneficiary.

The beneficiary's resource identifier, URI, address details (if stored) and bank details are returned.

The request requires that you provide the beneficiary resource ID:

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
<td markdown="span">You must reference a beneficiary</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/beneficiaries/{BENEFICIARY_ID}
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

<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#retrieve-beneficiary" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->


{% include links.html %}
