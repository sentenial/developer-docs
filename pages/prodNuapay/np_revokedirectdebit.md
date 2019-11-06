---
title: Revoke Direct Debit
keywords: Revoke Direct Debit
summary: "Revoke Direct Debit RESTful API"
sidebar: np_sidebar
permalink: np_revokedirectdebit.html
folder: prodNuapay
toc: false
---

## API Details

When you first create a Direct Debit it has a status of <b>READY FOR EXPORT</b>. Once it is forwarded from Nuapay on to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">Clearing</a> for processing, its status is updated to <b>EXPORTED</b>.

If you decide that you do not want to settle the payment and do not want to pass it on for further processing at Clearing, you may revoke it.


{% include tip.html content="The Revoke operation is only possible for payments that are in READY FOR EXPORT status. For more information see [Direct Debit Statuses](np_ddstatuses.html)." %}


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
<td markdown="span">The Revoke action is only possible on READY FOR EXPORT Direct Debits</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/mandates/{MANDATE_ID}/directdebits/{DD_ID}/revoke
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

<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#revoke-direct-debit" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->

{% include links.html %}
