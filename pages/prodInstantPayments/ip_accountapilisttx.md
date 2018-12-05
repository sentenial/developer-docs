---
title: List Transactions
keywords: List Account API
summary: "Use this service to retrieve transactions for a date range."
sidebar: ip_sidebar
permalink: ip_accountapilisttx.html
folder: prodNuapay
toc: false
---

## API Details

{% include note.html content="Before using this API request you must first retrieve the URI (the account identifier - {accountId}) for your Origix IP technical account. See [List Account](ip_accountapilist.html)." %} 

 The List Transactions service retrieves transactions for a required date range.


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
<td markdown="span">Use your {accountId} and specify a date range and/or an amount range to refine the list of transactions returned.</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/accounts/{accountId}/transactions/list
</td>
</tr>
<tr>
<td markdown="span">Optional Arguments</td>
<td markdown="span"><b>filter.valuedateFrom</b>
<br/><i>Epoch timestamp format; the date from which the transactions should be returned.</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>filter.valuedateTo</b>
<br/><i>Epoch timestamp format; the date up to when the balance should be returned.</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>filter.amountFrom</b>
<br/><i>The lower amount in the range.</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>filter.amountTo</b>
<br/><i>The higher amount in the range (Max amount 9,999,999,999.99).</i>
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 OK</b> response code</p>
Two key details are returned:
<ul>
<li><b>id</b>: A value that uniquely identifies the account in Origix IP.</li>
<li><b>uri</b>: A resolvable path containing the account. Use this in the List and View Transaction requests.</li>
</ul>

<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include httpcodes.html %}
    
 
    </div>


</div>


{% include links.html %}
