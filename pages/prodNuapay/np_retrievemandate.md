---
title: Retrieve Mandate
keywords: Retrieve Mandate API
summary: "Retrieve Mandate RESTful API"
sidebar: np_sidebar
permalink: np_retrievemandate.html
folder: prodNuapay
toc: false
---

## API Details

The Retrieve Mandate call allows you to view the details of a specific mandate as stored in Nuapay.

The request requires that you provide the Mandate resource identifier (as returned in the <a href="np_createmandate.html">Create Mandate</a> call)



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
<td markdown="span">You must reference a mandate ID</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates/{MANDATE_ID}
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span">No arguments are required
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

<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#retrieve-mandate" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->


{% include links.html %}
