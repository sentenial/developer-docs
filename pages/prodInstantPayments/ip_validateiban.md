---
title: Validate IBAN
keywords: SEPA Instant CT Validate IBAN
summary: "Retrieve SCT Instant RESTful API"
sidebar: ip_sidebar
permalink: ip_validateiban.html
folder: prodInstantPayments
toc: false
---

As Origix IP has no visibility of the accounts held by your financial institution, the system:

* Makes an API request to an Endpoint configured by your bank to validate the provided account.
* This configured Endpoint will need to consume the Origix IP requests to it and respond appropriately.
* If the account is matched on the Financial Institution / PSP and is valid to receive the SCT Inst payment then the Endpoint should respond to Origix IP with a 200 response code.
* Where the response to the Origix IP request is a 400 - Account is invalid (or a 500 - Server issue), the payment will not be credited and a REJECT notification will be dispatched from Origix IP to the CSM.

Accounts may fail validation for one of the following reasons (this code will be returned to the CSM in the negative confirmation message):

|**Return Code**|**Description**|
|AC01|Incorrect Account Number|
|AC04|Closed Account Number|
|AC06|Blocked Account|
|RC01|Bank Identifier Incorrect|
|AG01|Transaction Forbidden|
|MD07|End Customer Deceased|
|MS03|Not Specified Reason Agent Generated|
|AG02|Invalid Bank Operation Code|
|MS02|Not Specified Reason Customer Generated|
|RR04|Regulatory Reason|

## API Details

Origix IP will need to call the <b>Sepa Instant Payments Validation Service</b> which you will need to implement for your Bank/Financial Institution.
You (as the Creditor Bank) can define your own security header and value. The Origix IP application will add the header and value to every IBAN validation request sent towards your Bank. Please discuss your requirements with your Account Manager.

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
<td markdown="span">Origix IP will always include an IBAN, BIC and currency (default is EUR).</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/instantpayments/validate/
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 OK</b> response code.</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
      
      
<table>
<colgroup>
<col width="10%" />
<col width="70%" />
</colgroup>
<thead>
<tr class="header">
<th>Status Code</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td markdown="span">200</td>
<td markdown="span">OK - The request completed successfully.</td>
</tr>
<tr>
<td markdown="span">400</td>
<td markdown="span">Account is invalid. Valid codes: AC01, AC04, AC06, RC01, AG01, MD07, MS03, AG02, MS02, RR04 (see the table above for descriptions)
</td>
</tr>
<tr>
<td markdown="span">500</td>
<td markdown="span">Server could not process the request.
</td>
</tr>
</tbody>
</table>
      
    
    
    </div>


</div>

<p><b>Note</b>: For a more detailed view of this API see the OpenAPI/Swagger redoc: <a href="https://docs.sentenialtest.com/sip-docs/redoc.html?url=/sip-docs/SIP_REST_Endpoints.json#operation/GetInstantPaymentsUsingGET" target = "_blank"><i class="fa fa-cogs"></i> OpenAPI/Swagger Reference</a> </p>


{% include links.html %}
