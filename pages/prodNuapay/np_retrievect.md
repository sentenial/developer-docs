---
title: Retrieve Credit Transfer
keywords: Retrieve Credit Transfer
summary: "Retrieve Credit Transfer RESTful API"
toc: false
sidebar: np_sidebar
permalink: np_retrievect.html
folder: prodNuapay
toc: false
---

## API Details

The Retrieve Credit Transfer request allows you return the details of a given Credit Transfer payment.

The payment's ID, URI, end-to-end, requested execution date etc. are all returned.

The request requires that you provide the:

* Beneficiary Resource ID
* Credit Transfer Resource ID


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
<td markdown="span">You must reference a beneficiary and a Credit Transfer</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/beneficiaries/{BENEFICIARY_ID}/credittransfers/{CT_ID}
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


<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#retrieve-credit-transfer" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->

{% include links.html %}
