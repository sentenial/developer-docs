---
title: View Transaction
keywords: View Transactions API
summary: "Use this service to view the details of a single transaction."
sidebar: ip_sidebar
permalink: ip_accountapiviewtx.html
folder: prodNuapay
toc: false
---

## API Details

{% include note.html content="Before using this API request you must first retrieve the URI (the account identifier - {accountId}) for your Origix IP technical account; see [List Account](ip_accountapilist.html). You will also need a specific transaction ID, returned in the [List Transactions](ip_accountapilisttx.html) request." %} 

 The View Transaction service retrieves an individual transaction.


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
<td markdown="span">Use your {accountId} and a {transactionId} to retrieve the details of a single transaction.</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/accounts/{accountId}/transactions/{transactionId}
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
