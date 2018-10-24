---
title: Uploading a Contract
keywords: Uploading Contract Upload
summary: "Uploading a contract PDF is required as an initial step before combining it with a mandate."
sidebar: em_sidebar
permalink: em_contractupload.html
folder: prodEmandates
---

To upload a contract, use the <b>Upload Contract</b> request.








{% include note.html content="Contracts must be saved in PDF and we recommend that the file size does not exceed 1 MB." %}





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
<td markdown="span">The contract must be a PDF file (application/pdf)</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/contracts
</td>
</tr>
<tr>
<td markdown="span">Optional Arguments</td>
<td markdown="span">fileName: If not provided the name of the uploaded file is used. <br/><br/>contractType: OOFF or RCUR<br/><br/> Contracts can be either once-off or recurring: Once-Off (OOFF) contracts are just used once in a single signing operation.
Recurring (RCUR) contracts can be re-used in multiple signing operations; this is useful where your business use a standard contract and you want to offer all your customers the same PDF contract document.
</td>
</tr>
</tbody>
</table>

<p>Request Sample</p>
{% gist 965035bdbb5a6ebe4b592e0c206fb81b %}



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>200 Created</b> response code</p>
<p>Response Sample</p>

{% gist 7ad94961a01a55a2ac75948acf39c085 %}

<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include httpcodes.html %}
    

 
    </div>


</div>

Once you have retrieved your contract identifier you can use it in your Prepare E-Mandate request in your chosen integration approach:

 

* <a href="em_tokenredirect.html">Redirect</a>
* <a href="em_token.html">Overlay</a>
* <a href="em_tokendirectapi.html">Direct API Integration</a>



{% include links.html %}
