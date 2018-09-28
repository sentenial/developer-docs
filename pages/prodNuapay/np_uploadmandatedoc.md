---
title: Upload Mandate Document
keywords: Upload Mandate Document API
summary: "Upload Mandate Document RESTful API"
sidebar: np_sidebar
permalink: np_uploademandatedoc.html
folder: prodNuapay
toc: false
---

## API Details

If you want to upload a representation of the mandate, for example if you have a signed paper mandate, have scanned it and saved it as a PDF, you can upload this to Nuapay so that it is linked to the required mandate.

This can then be viewed later if you use the <a href = "np_retrievemandatedoc.html"> Retrieve Mandate Document</a> call.

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
<td markdown="span">You may reference a mandate in any status</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates/{MANDATE_ID}/document
</td>
</tr>
<tr>
<td markdown="span">File Content Types</td>
<td markdown="span">application/pdf... image/jpg...image/gif
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
