---
title: Create Instant Payment
keywords: SEPA Instant CT Create
summary: "Create SCT Instant RESTful API"
sidebar: ip_sidebar
permalink: ip_createinstct.html
folder: product2
toc: false
---


Use the Create Instant Payment service to create an SCT Inst instruction in Origix IP.


## API Details



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
<td markdown="span">The beneficiary bank should be able to process SEPA CT Instant payments. If it cannot your payment will fail wtth a reachability error.</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/instantpayments
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span"><b>interBankSettlementAmount</b>
<br/><i>The amount</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>paymentIdentifiers</b>
<br/><i>The end-to-end and the transaction identifiers are both mandatory.</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>debtor</b>
<br/><i>The debtor's name is mandatory; the debtor address is optional and also available under this object.</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>debtorAccount</b> 
<br/><i>The debtor account details are required.</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>creditor</b>
<br/><i>The creditor's name is required; the creditor address is optional and also available under this object.</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>creditorAccount</b> 
<br/><i>The creditor account details are required.</i>
</td>
</tr>
</tbody>
</table>

</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>201 Created</b> response code</p>
Details returned in the response include:

<table>
<colgroup>
<col width="30%" />
<col width="90%" />
</colgroup>

<tbody>
<tr>
<td markdown="span">id</td>
<td markdown="span">A value that uniquely identifies the payment in Origix IP.</td>
</tr>
<tr>
<td markdown="span">uri</td>
<td markdown="span">A resolvable path that uniquely identifies the SCT Inst instruction in Origix IP. Use this value to Retrieve an Instant Payment.
</td>
</tr>
<tr>
<td markdown="span">paymentStatus</td>
<td markdown="span">The current status of the payment (initially PENDING)
</td>
</tr>
<tr>
<td markdown="span">accptncDtTm</td>
<td markdown="span">The timestamp added to the SCT Inst Instruction.
</td>
</tr>
<tr>
<td markdown="span">paymentDetails</td>
<td markdown="span">Payment-related details including the settlement amount, payment identifiers, debtor details, creditor details and remittance information.
</td>
</tr>
<tr>
<td markdown="span">rejectDetails</td>
<td markdown="span">Where the SCT Inst instruction fails, the reject reason, description and type are all returned.
</td>
</tr>
</tbody>
</table>


<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include httpcodes.html %}
    
 
    </div>


</div>

{% include swaggerlink.html %}

{% include links.html %}
