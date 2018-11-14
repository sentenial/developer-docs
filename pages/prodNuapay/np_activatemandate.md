---
title: Activate Mandate
keywords: sample
summary: "Activate Mandate RESTful API"
sidebar: np_sidebar
permalink: np_activatemandate.html
folder: prodNuapay
toc: false
---

## API Details

<p>Where a mandate is in Pending or Suspended <a href="np_mandatestatuses.html">status</a> you can set it to Active so that Direct Debit Payments can be made against it.</p>

<p>If you are using paper mandates then you may need to consider an option on your custom application to allow operators to click a button to activate mandates when a signed mandate is received, which would call this request.</p>

<p>If you are using E-Mandates, the activate mandate request is dynamically called and may (optionally) include details related to the electronic signing event (IP Address, location of the signature, the mobile phone or email address used)</p>



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
<td markdown="span">Mandates must be in PENDING or SUSPENDED status</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates/{MANDATE_ID}/activate
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

<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#activate-mandate" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->

{% include links.html %}
