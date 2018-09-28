---
title: List Creditor Schemes
keywords: List Creditor Schemes API
summary: "List Creditor Schemes RESTful API"
sidebar: np_sidebar
permalink: np_listcredscheme.html
folder: prodNuapay
toc: false
---

## API Details

<p>All mandates that you create (and all subsequent Direct Debit payments) must be linked to a unique Creditor Scheme Identifier (CSID). </p>

<p>This identifier (and its resource identifier) will be provided to you by Nuapay when you register or, if you have processed Direct Debit payments with another provider, you may already have a CSID that you may reuse in Nuapay. </p>
<p>If you already have a CSID you will need to use List Creditor Schemes to retrieve its Nuapay resource identifier. </p>

{% include note.html content="You must use the resource identifier of the scheme in your requests. This identifier will be similar to this abxq9kq52l; do not reference the actual creditor scheme ID in your requests." %}

<p>If you lose this reference or if you have multiple CSIDs and want to review them all, you can use the List Creditor Schemes request. You will use this resource identifier CSID in all subsequent Mandate and Direct Debit requests.</p>



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
<td markdown="span">Generally you will just need to make this request once</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 Created</b> response code</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include httpcodes.html %}
    
 
    </div>


</div>

{% include swaggerlink.html %}

{% include links.html %}
