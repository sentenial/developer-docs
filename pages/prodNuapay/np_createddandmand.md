---
title: Create Direct Debit & Mandate
keywords: Create Direct Debit & Mandate
summary: "Create Direct Debit & Mandate RESTful API - generate a mandate and a payment in a single API call."
sidebar: np_sidebar
permalink: np_createddandmand.html
folder: prodNuapay
toc: false
---

## API Details

As outlined in the <a href= "np_createdirectdebit.html"> Create Direct Debit</a> call, you must have an active mandate before you can begin to collect Direct Debit payments. Typically you would use the <a href="np_createmandate.html">Create Mandate</a> call and then reference the successfully activated mandate when you create the Direct Debit payment.

The <b>Create Direct Debit and Mandate</b> call allows you to combine these separate requests into a single call; the request performs two operations:

* A mandate is created in Active status
* A Direct Debit payment is created and linked to the new mandate


{% include note.html content="A successful request will result in a new mandate and direct debit being created. If the request is unsuccessful neither a mandate nor a direct debit will be created." %}


The Create Direct Debit and Mandate request must include:

* A requested collection date for the Direct Debit payment
* The payment amount
* The payer's name
* The payer's IBAN
* The Merchant Nuapay IBAN

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
<td markdown="span">The requested collection date and amount are required along with the mandate details.</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/directdebits
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
