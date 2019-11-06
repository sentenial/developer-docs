---
title: Create Beneficiary
keywords: Create Beneficiary
summary: "Create Beneficiary RESTful API"
sidebar: np_sidebar
permalink: np_createbeneficiary.html
folder: prodNuapay
toc: false
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %} 

Unlike the Direct Debit payment API, Beneficiary and CT requests do not require a Creditor Scheme ID reference.

Before you can initiate a payment via the Create Credit Transfer request you must first create a beneficiary. 
Alternatively it is possible to generate a new beneficiary and a payment in a single request. See the <a href ="np_createctandbene.html">Create Credit Transfer and Beneficiary</a> request.

{% include note.html content="at its most basic, a beneficiary requires a name and a bank account reference. Additional data may also be stored but is not mandatory (address details and contact details, for example)" %}

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
<td markdown="span">You must provide the name and the account details to create a beneficiary</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/beneficiaries
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span">beneficiary.name, beneficiaryAccount.iban
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

<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#create-beneficiary" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->

{% include links.html %}
