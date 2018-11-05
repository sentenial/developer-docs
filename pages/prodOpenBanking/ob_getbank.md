---
title: Retrieve Banks
keywords: Retrieve Banks Open Banking 
summary: "Retrieve Bank RESTful API"
sidebar: ob_sidebar
permalink: ob_getbank.html
folder: prodOpenBanking
toc: false
---

## API Details

Before you can initiate an account access request to your customer you must first offer the customer a choice of available banks. This service allows you to retrieve a list of banks participating in Open Banking.


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
<td markdown="span">This service returns all Nuapay TPP particiapting banks.</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/banks
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 Banks retrieved</b> response code</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include ob_httpcodes.html %}
    
 
    </div>


</div>

<p><b>Note</b>: For a more detailed view of this API see the OpenAPI/Swagger redoc: <a href="https://sentenial.github.io/open-banking-swagger/docs/redoc.html#operation/getBanksUsingGET" target = "_blank"><i class="fa fa-cogs"></i> OpenAPI/Swagger Reference</a> </p>

{% include links.html %}
