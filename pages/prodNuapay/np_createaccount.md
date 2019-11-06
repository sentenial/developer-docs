---
title: Create Account
keywords: Create Account
summary: "Create Account RESTful API"
sidebar: np_sidebar
permalink: np_createaccount.html
folder: prodNuapay
toc: false
---

## API Details

The Create Account request allows you to generate a new Nuapay account. You may create a current account or (optionally and depending on your merchant configuration) a sub-account.

{% include important.html content="It is possible to generate a Master or a Sub-Account. Note that sub-accounts may only be used for processing Credit Transfer payments. Note too that your merchant must be configured by Nuapay Client Services team to allow you to create a sub-account. For more information please contact your Account Manager." %}

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
<td markdown="span">You must provide an Account Name and currency (EUR or GBP)</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/accounts
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>201 Created</b> response code</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include httpcodes.html %}
    
 
    </div>


</div>


<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#create-account" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->

{% include links.html %}
