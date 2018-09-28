---
title: List Mandates
keywords: List Mandates API
summary: "List Mandates RESTful API"
sidebar: np_sidebar
permalink: np_listmandates.html
folder: prodNuapay
toc: false
---

## API Details

The List Mandates request allows you to view a collection of mandates linked to a:

* Specific Scheme
* All schemes (i.e. all mandates)

Use an appropriate URI (as described below) to return the required collection of Mandates.


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
<td markdown="span">You can return all mandates or filter based on scheme</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-success">GET </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates 
</td>
</tr>
<tr>
<td markdown="span">(Or)</td>
<td markdown="span">/mandates
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
