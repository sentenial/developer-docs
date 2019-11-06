---
title: Retrieve Mandate Document
keywords: Retrieve Mandate Document API
summary: "Retrieve Mandate Document RESTful API"
sidebar: np_sidebar
permalink: np_retrievemandatedoc.html
folder: prodNuapay
toc: false
---

## API Details

All Mandates include a PDF representation of the mandate data. If required you may upload a different representation of a mandate if required (PDF, JPG and GIF formats are all supported).

The Retrieve Mandate Document call allows you to access the file representation of the mandate.

{% include urls.html %}

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
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates/{MANDATE_ID}/document
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 OK</b> response code along with the PDF, JPG or GIF binary content.</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
      {% include httpcodes.html %}
    
    
    </div>


</div>

<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#retrieve-mandate-document" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->



{% include links.html %}
