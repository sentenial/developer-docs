---
title: Update Mandate
keywords: Update Mandates API
summary: "Update Mandates RESTful API"
sidebar: np_sidebar
permalink: np_updatemandate.html
folder: prodNuapay
toc: false
---

## API Details

You may need to make updates to mandates at various points. Where a payer informs you that address details or an account has changed, for example, it is important to update this data so that Direct Debit payments will continue to be processed as normal.

You may need to re-send the mandate for signature depending on the update that is being made to the mandate. 
We would recommend that a mandate is approved by your payer if any of the following <b>key mandate fields</b> are modified:

* The Unique Mandate Reference (the SEPA Mandate ID)
* Payer account data


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
<td markdown="span">You can update mandates in Pending and Active status</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-primary">PUT </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates/{MANDATE_ID}
</td>
</tr>
</tbody>
</table>

<p>The <b>mandateInfo.resendMandateForSignature</b> argument allows you to control if your payer should re-sign the updated mandate: </p>

<table>
<colgroup>
<col width="30%" />
<col width="90%" />
</colgroup>

<tbody>
<tr>
<td markdown="span">DEFAULT</td>
<td markdown="span">the mandate is updated from Active to Pending if a key mandate field (see above) is modified .</td>
</tr>
<tr>
<td markdown="span">SEND</td>
<td markdown="span">the mandate is always updated from Active to Pending for any mandate update.
</td>
</tr>
<tr>
<td markdown="span">DO_NOT_SEND</td>
<td markdown="span">the mandate remains in Active status regardless of the modification to the mandate.
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

{% include swaggerlink.html %}


{% include links.html %}
