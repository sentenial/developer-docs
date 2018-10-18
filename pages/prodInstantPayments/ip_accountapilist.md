---
title: List Account
keywords: List Account API
summary: "Use this service to retrieve the URI of your Origix IP Technical Account (or Shadow Account). This is required for subsequent calls to other Account services."
sidebar: ip_sidebar
permalink: ip_accountapilist.html
folder: prodNuapay
toc: false
---

## API Details

Use the List Account service to retrieve the URI for your Origix IP Technical account.

This URI will be used later in the List Transactions and View Transaction API requests.



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
<td markdown="span">The request is used to retrieve the encoded URI for your configured shadowing account.</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/accounts/list
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

{% include swaggerlink.html %}

{% include links.html %}
