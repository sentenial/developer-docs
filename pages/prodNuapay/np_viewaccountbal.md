---
title: List Account Balances
keywords: List Account Balances
summary: "List Account Balances RESTful API"
toc: false
sidebar: np_sidebar
permalink: np_listaccountbal.html
folder: prodNuapay
toc: false
---

## API Details

Use this request to return the balance on a specific account.

{% include note.html content="This request uses the dateuntil parameter. This takes a Unix Epoch timestamp and defaults to the current date" %}



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
<td markdown="span">Supply an epoch value to return the balance for a specific timestamp</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/accounts/{ACCOUNT_ID}/balances
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

<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#list-account-balances" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->


{% include links.html %}
