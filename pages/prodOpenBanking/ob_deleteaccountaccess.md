---
title: Delete Account Access
keywords: Delete Account Access Open Banking 
summary: "Delete Account Access RESTful API"
sidebar: ob_sidebar
permalink: ob_deleteaccountaccess.html
folder: prodOpenBanking
toc: false
---

## API Details

Use this service to delete an account access request previously generated (see the [Create Account Access](ob_createaccountaccess.html) request). 
This service will typically be required where a customer has asked for the account access previously granted to be revoked.



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
<td markdown="span">Provide the URI of the required account. </td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-danger">DELETE </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/account-requests/{accountRequestReference}
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span"><b>accountRequestReference</b>
<br/><i>Unique identification as assigned by TPP to uniquely identify the account request resource.</i>
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>201 Created</b> response code</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include ob_httpcodes.html %}
    
 
    </div>


</div>

{% include ob_swaggerlink.html %}

{% include links.html %}
