---
title: Create Mandate/DDI
keywords: Mandate DDI Create Initiate Begin
summary: "Create Mandate RESTful API"
sidebar: np_sidebar
permalink: np_createmandate.html
folder: prodNuapay
toc: false
---


{% include tip.html content="If you are using E-Mandates you do not need to use this Create Mandate request." %}


## API Details

When creating mandates/DDIs, please note that:

* Mandates/DDIs must be created under a specific scheme (e.g. the SEPA CORE or Bacs scheme) and must also be linked to a Creditor Scheme ID (CSID) in SEPA or a Service User Number (SUN) for Bacs.
* To determine your CSID/SUN use the [List Scheme](np_listcredscheme.html) service.  
* Depending on the configuration of your Creditor Scheme your mandates/DDI will be created in a specific [status](np_mandatestatuses.html).
* Regardless of the scheme, Direct Debit payments can only be created against an **ACTIVE** mandate/DDI.

## A Note on the Mandate Identifier in the Bacs Scheme

A unique mandate (DDI) identifier (also known as the Core Reference in Bacs), the `mandateId` is applied automatically when you call the Create Mandate/DDI endpoint.

If required you may also specify this identifier in your request.

If you want to assign your own `mandateId` when adding a mandate/DDI against the Bacs scheme, please note:

* The `mandateId` must > 6 alphanumeric characters. ABC-12-3 for example would be evaluated as having a length = 6 characters (ABC123; the Hyphens are not included in the character count).
* The total length of the `mandateId` cannot exceed 18 characters.
* It cannot consist of all the same characters e.g. all zeros.
* It must be unique for the sort code, account number and SUN.
* The following non-alphanumeric characters are supported and may be used in the identifier:
  * Full stop(.)
  * Slash (/)
  * Hyphen (-)
  * Blank space ( )
* It cannot begin with the letters DDIC.

## The DDI Reference and End-to-End Identifiers in Bacs

Later when you create a Direct Debit payment against your DDI, in the Bacs scheme, the transaction will use the DDI reference (`mandateId`) as its starting code.
So for a mandate/DDI = `ABCDEF123`, its linked transactions could have identifiers as follows:

* ABCDEF12301
* ABCDEF12302
* ABCDEF12303

For this reason we recommend that your `mandateId` should not use all 18 characters as this will mean that reconciling individual transactions later will be made more difficult (as in this case all transactions would have the same `endToEndId`).

{% include tip.html content="If in any doubt allow Nuapay to automatically assign the `mandateId`; your DDI reference will be correctly formatted and you can be confident that your reference will not be in breach of any Bacs guidelines, which could potentially result in failed payments later." %}


{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addMandateUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
