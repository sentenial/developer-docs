---
title: Create Account Access
keywords: Create Account Access Open Banking 
summary: "Create Account Access RESTful API"
sidebar: ob_sidebar
permalink: ob_createaccountaccess.html
folder: prodOpenBanking
toc: false
---

## API Details

The Create Account Access service generates the account request that the end user must agree to in order for you, as merchant, to access specific account details.

{% include tip.html content="You must know the bank in which your customer's account is held; this is passed as the <b>x-tpp-bank-id</b> value in your API Header parameter. Use the <b>GET /banks</b> service to retrieve the required Bank ID. " %}



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
<td markdown="span">An appropriate Bank ID must be provided as a Header in your request. </td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/account-requests
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span"><b>merchantPostAuthUrl</b>
<br/><i>the merchant url to hit post authorization step</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>permissions</b>
<br/><i>An array of values are possible which specify the Open Banking account request types. This is a list of the data clusters being consented by the PSU, and requested for authorisation with the ASPSP. Valid items: <br/> <i><span _ngcontent-c21="" class="param-enum-value string"> "ReadAccountsBasic" </span>"ReadAccountsBasic" "ReadAccountsDetail" "ReadBalances" "ReadBeneficiariesBasic" "ReadBeneficiariesDetail" "ReadDirectDebits" "ReadProducts" "ReadStandingOrdersBasic" "ReadStandingOrdersDetail" "ReadTransactionsBasic" "ReadTransactionsCredits" "ReadTransactionsDebits" "ReadTransactionsDetail"</i> </i>
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
