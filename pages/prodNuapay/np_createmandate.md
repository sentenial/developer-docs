---
title: Create Mandate/DDI
keywords: Mandate DDI Create Initiate Begin
summary: "Create Mandate RESTful API"
sidebar: np_sidebar
permalink: np_createmandate.html
folder: prodNuapay
toc: true
---


{% include tip.html content="If you are using E-Mandates you do not need to use this Create Mandate request." %}


## API Details

When creating mandates/DDIs, please note that:

* Mandates/DDIs must be created under a specific scheme (e.g. the SEPA CORE or Bacs scheme) and must also be linked to a Creditor Scheme ID (CSID) in SEPA or a Service User Number (SUN) for Bacs.
* To determine your CSID/SUN use the [List Scheme](np_listcredscheme.html) service.  
* Depending on the configuration of your Creditor Scheme your mandates/DDI will be created in a specific [status](np_mandatestatuses.html).
* Regardless of the scheme, Direct Debit payments can only be created against an **ACTIVE** mandate/DDI.

{% include idempotency.html %} 

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

## Managing Address Details in SEPA

The European Payments Council (EPC), which manages SEPA rules, has specific guidelines for how addresses must be formatted and provided. Please review the following points to ensure that your payment files remain compliant and avoid bank rejections.

## Structured / Unstructured / Hybrid Address Formats
Addresses in SEPA payments can be Structured, Unstructured or Hybrid.

**Structured**: Every address component has a dedicated field (Street, Building Number, Postcode, etc.). In payments files, each element is placed in its own dedicated XML tag. This is the most reliable format and the eventual industry standard.

**Unstructured**: Address details are provided as a single block of free text using "Address Lines." Note: This format is currently being phased out in favor of structured data. After November 16th 2026, purely unstructured addresses will not be permitted.

**Hybrid**: A transitional format that combines mandatory structured tags (Country and Town) with unstructured "Address Lines" for the remaining details. This serves as a bridge for systems not yet ready for full structural mapping.

The following table summarises the valus that are possible with each address format, with the mandatory and optional elements:

| Element               | XML Tag        | Unstructured | Structured | Hybrid | Mandatory Status                     |
|-----------------------|----------------|--------------|------------|--------|--------------------------------------|
| Country               | Ctry           | ✔︎           | ✔︎         | ✔︎     | Mandatory (Always)                   |
| Address Line          | AdrLine        | ✔︎           | ✘          | ✔︎     | Mandatory (Unstructured)             |
| Town Name             | TwnNm          | ✘            | ✔︎         | ✔︎     | Mandatory (Structured, Hybrid)       |
| Street Name           | StrtNm         | ✘            | ✔︎         | ✔︎     | Optional                             |
| Post Code             | PstCd          | ✘            | ✔︎         | ✔︎     | Optional                             |
| Building Number       | BldgNb         | ✘            | ✔︎         | ✔︎     | Optional                             |
| Building Name         | BldgNm         | ✘            | ✔︎         | ✔︎     | Optional                             |
| Floor                 | Flr            | ✘            | ✔︎         | ✔︎     | Optional                             |
| Unit Number           | UnitNb         | ✘            | ✔︎         | ✔︎     | Optional                             |
| Room                  | Room           | ✘            | ✔︎         | ✔︎     | Optional                             |
| Post Box              | PstBx          | ✘            | ✔︎         | ✔︎     | Optional                             |
| Department            | Dept           | ✘            | ✔︎         | ✔︎     | Optional                             |
| Sub-Department        | SubDept        | ✘            | ✔︎         | ✔︎     | Optional                             |
| District Name         | DstrctNm       | ✘            | ✔︎         | ✔︎     | Optional                             |
| Town Location         | TwnLctnNm      | ✘            | ✔︎         | ✔︎     | Optional                             |
| Country Sub-Division  | CtrySubDvsn    | ✘            | ✔︎         | ✔︎     | Optional                             |


### Transactions Involving Non-European-Ecomomic-Area (EEA) Countries
If either you or your debtor is located outside the EEA, you must provide debtor address information under the Wire Transfer Regulation (WTR). This EU law ensures transparency for fraud prevention and anti-money laundering (AML) efforts.

|**Best Practice**: While Town and Country are the technical minimums for structured addresses, we strongly recommend providing additional elements (such as `Street Name` and `Building Number`) to reduce the risk of manual intervention or payment rejection by the intermediary or beneficiary bank.|

### Transactions Within the EEA
If both you and your debtor are located within the EEA, providing an address for the debtor is not mandatory.

If you choose to provide an address voluntarily (where not strictly required by the WTR), ensure that you meet the mandatory elements as outlined in the table above.


{% include swagger_np.html %}

{% include urls.html %}
{% include tip.html content="You must use the resource identifier of the `schemeId` in your request and not the actual creditor scheme ID or SUN. This identifier will be similar to this: abxq9kq52l - so in this case you would call POST /schemes/abxq9kq52l/mandates. See [List Schemes](np_listcredscheme.html) for more on this." %}



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
