---
title: Retrieve Account Transactions
keywords: Retrieve Account Transactions Open Banking 
summary: "Retrieve Account Transactions RESTful API"
sidebar: ob_sidebar
permalink: ob_getaccounttx.html
folder: prodOpenBanking
toc: false
---

## API Details

Returns the list of transactions linked to a specified account.


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
<td markdown="span">Provide the account id. </td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/accounts/{accountId}/standing-orders
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span"><b>accountId</b>
<br/><i>A unique identifier used to identify the account resource. (Only mandatory for /accounts/{accountId}) </i>
</td>
</tr>

<tr>
<td markdown="span">Optional Arguments</td>
<td markdown="span"><b>amount</b>
<br/><i>The amount</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>page</b>
<br/><i>The page of results we are looking for (results per page is dynamic and bank dependant), defaults to the first page.</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>fromBookingDateTime</b>
<br/><i>The UTC ISO 8601 Date Time to filter transactions FROM NB Time component is optional - set to 00:00:00 for just Date. The parameter must NOT have a timezone set</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>toBookingDateTime</b> 
<br/><i>The UTC ISO 8601 Date Time to filter transactions TO NB Time component is optional - set to 00:00:00 for just Date. The parameter must NOT have a timezone set</i>
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 Account Transactions retrieved</b> response code</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include ob_httpcodes.html %}
    
 
    </div>


</div>

{% include swaggerlink.html %}

{% include links.html %}
