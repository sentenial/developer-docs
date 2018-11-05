---
title: Retrieve Payment
keywords: Retrieve Open Banking Payment
summary: "Retrieve Open Banking Payment RESTful API"
sidebar: ob_sidebar
permalink: ob_retrievepayment.html
folder: prodOpenBanking
toc: false
---

## API Details

The Retrieve Payment service returns an Open Banking payment object, where the unique ``paymentId`` is provided.



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
<td markdown="span">You must pass the paymentId.</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/payments/{paymentId}
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 resource retrieved</b> response code, including details of the payment - status, amount, currency etc.</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include ob_httpcodes.html %}
    
 
    </div>


</div>

<p><b>Note</b>: For a more detailed view of this API see the OpenAPI/Swagger redoc: <a href="https://sentenial.github.io/open-banking-swagger/docs/redoc.html#operation/getUsingGET" target = "_blank"><i class="fa fa-cogs"></i> OpenAPI/Swagger Reference</a> </p>

{% include links.html %}
