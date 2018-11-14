---
title: Create Mandate
keywords: sample
summary: "Create Mandate RESTful API"
sidebar: np_sidebar
permalink: np_createmandate.html
folder: product2
toc: false
---


{% include tip.html content="If you are using E-Mandates you do not need to use this Create Mandate request." %}


## API Details

<p>Mandates must be created under a specific scheme (typically the SEPA CORE scheme) and must also be linked to a Creditor Scheme ID (CSID). (To determine your CSID use the <a href="np_listcredscheme.html"> List Creditor Schemes</a> API request).</p> 
<p>Depending on the configuration of your Creditor Scheme your mandates will be created in a specific status. Note that Direct Debit payments can only be created against an Active mandate.</p>



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
<td markdown="span">Mandates must be created under a CSID.</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span">debtor.name, debtorAccount.iban, creditorAccount.iban
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

<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#create-mandate" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->

{% include links.html %}
