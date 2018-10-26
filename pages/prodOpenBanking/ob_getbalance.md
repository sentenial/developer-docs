---
title: Retrieve Account Balance
keywords: Retrieve Account Balance Open Banking 
summary: "Retrieve Account Balance RESTful API"
sidebar: ob_sidebar
permalink: ob_getbalance.html
folder: prodOpenBanking
toc: false
---

## API Details

Return the current balance on a specified account.


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
<td markdown="span">/accounts/{accountId}/balances
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span"><b>accountId</b>
<br/><i>A unique identifier used to identify the account resource. (Only mandatory for /accounts/{accountId}) </i>
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 Account Balance retrieved</b> response code</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include ob_httpcodes.html %}
    
 
    </div>


</div>

{% include ob_swaggerlink.html %}

{% include links.html %}
