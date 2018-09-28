---
title: Retrieve Direct Debit
keywords: Retrieve Direct Debit
summary: "Retrieve Direct Debit RESTful API"
toc: false
sidebar: np_sidebar
permalink: np_retrievedirectdebit.html
folder: prodNuapay
toc: false
---

## API Details

The Retrieve Direct Debit request allows you return the details of a given Direct Debit payment.

The payment's ID, URI, end-to-end, collection date etc. are all returned.

The request requires that you provide the:

* Resource Mandate ID
* Resource Direct Debit ID


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
<td markdown="span">You must reference a mandate and a Direct Debit linked to that mandate</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates/{MANDATE_ID}/directdebits/{DD_ID}
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
