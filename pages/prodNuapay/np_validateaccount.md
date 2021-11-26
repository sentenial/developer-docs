---
title: Account Validation
keywords: Validate IBAN BBAN
summary: "The Validate Account service allows you to pass either domestic account details (to validate and retrieve an IBAN) or to pass an IBAN (to validate and retrieve the domestic account details). "
sidebar: np_sidebar
permalink: np_validateaccount.html
folder: prodNuapay
toc: false
---

## API Details

The Validate Account service allows you to:

* Validate an IBAN.
* Validate a domestic account.

{% include tip.html content="When validating a domestic account, depending on the country selected, certain arguments may or may not be required. For a Spanish domestic account, for example, Account Number, Bank Code, Branch Code and Check Sum are all required; for an Irish or UK account just the Account Number and Branch Code are mandatory. " %}



{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/validateDomesticAccountUsingPOST','#profileTabs',timerRef); }, 500);


</script>



<!--
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
<td markdown="span">Pass either an IBAN or the domestic account number, country and other required parameters, based on the country selected.</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/iban/validate
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span"><b>domesticAccountNumber</b>
<br/><i>The account number. Only required if validating a domestic account</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>accountCountry</b>
<br/><i>The ISO country code. Only required if validating a domestic account.</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>iban</b>
<br/><i>The account in IBAN format. A required argument if you are validating an IBAN.</i>
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

<p><b>Note</b>: For a more detailed view of this API see the OpenAPI/Swagger redoc: <a href="https://sentenial.github.io/open-banking-swagger/docs/redoc.html#operation/createPaymentUsingPOST " target = "_blank"><i class="fa fa-cogs"></i> OpenAPI/Swagger Reference</a> </p>



{% include links.html %}
-->
