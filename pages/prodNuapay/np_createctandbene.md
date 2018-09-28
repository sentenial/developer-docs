---
title: Create Credit Transfer & Beneficiary
keywords: Create Credit Transfer & Beneficiary
summary: "Create Credit Transfer & Beneficiary RESTful API - generate a payment and its beneficiary in a single API call."
sidebar: np_sidebar
permalink: np_createctandbene.html
folder: prodNuapay
toc: false
---

## API Details

The Create Credit Transfer request requires that you have first created a beneficiary. In some scenarios it is simpler to generate both the beneficiary and the payment at the same time and this request allows you to do that. 

{% include important.html content="If the beneficiary details you reference in the request have been previously provided (and that beneficiary is already stored against your merchant profile) Nuapay will reuse that stored beneficiary data: a new beneficiary is only created if his/her beneficiary account has not been referenced before in a previous Credit Transfer payment." %}

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
<td markdown="span">Both beneficiary and payment details must be provided.</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/credittransfers
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span">beneficiary.name, beneficiaryAccount.iban, originatorIban, paymentAmount, paymentCurrency
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

{% include swaggerlink.html %}

{% include links.html %}
