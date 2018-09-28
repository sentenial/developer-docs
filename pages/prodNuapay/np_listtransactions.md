---
title: List Transactions
keywords: List Transactions API
summary: "List Transactions RESTful API"
sidebar: np_sidebar
permalink: np_listtransactions.html
folder: prodNuapay
toc: false
---

## API Details

The List Transactions request allows you to view all the transactions linked to a specific Nuapay merchant account.

{% include note.html content="Because there are no required fields in this request, if you do not want to provide any parameters, you must supply an empty JSON body using {}. Filtering based on timestamps and based on the value of the transactions is also possible." %}

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
<td markdown="span">Optionally Set the date range and amounts required</td>
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
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 OK</b> response code.</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
      {% include httpcodes.html %}
    
    
    </div>


</div>

{% include swaggerlink.html %}


{% include links.html %}
