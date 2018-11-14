---
title: E-Mandate Token
keywords: E-Mandate Token
summary: "The session identifier or token required to initiate the e-mandate conversation."
sidebar: em_sidebar
permalink: em_tokenredirect.html
folder: prodEmandates
---

An E-Mandate token is a session ID that is the starting point for your electronic mandate.

The Token encapsulates the following:

* Your Merchant configurations (Signing Method, UI customisations, Debtor/Payer Input Allowed, etc.)
* Merchant-specific details (Creditor Scheme ID, Scheme Type, etc.)
* Payer details (Address details, phone details, email, etc.)
* Contract Identifier (optional, if you want to combine a contract and mandate - see <a href="#">E-mandate and Contract</a>)

{% include note.html content="Because we use tokens, your customers' sensitive account details are never stored on your server." %}

To retrieve your token you must make a <b>Prepare E-Mandate</b> request:




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
<td markdown="span">You must have a unique token in order to create an electronic mandate</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/emandates
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span"><b>merchantDetails.iban</b>
<br/><i>The merchant IBAN</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>merchantDetails.creditorSchemeId</b>
<br/><i>(use <a href="np_listcredscheme.html">List Creditor Schemes</a> to retrieve your CSID)</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>merchantDetails.schemeType</b>
<br/><i>(CORE, B2B, BACS)</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>merchantDetails.mandateType</b>
<br/><i>(Use either OOFF (for a once-off mandate; only one Direct Debit payment may be made against a OOFF mandate) or RCUR (a recurring mandate; more than one Direct Debit payment may be made against the mandate))</i>
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



<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/emandate-api/#prepare-e-mandate" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


{% include links.html %}
