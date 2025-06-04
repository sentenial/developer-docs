---
title: Create Direct Debit
keywords: Create Direct Debit
summary: "Create Direct Debit RESTful API"
sidebar: np_sidebar
permalink: np_createdirectdebit.html
folder: prodNuapay
toc: true
---

## API Details

The Create Direct Debit request must:

* Include the resource identifier Creditor Scheme ID (CSID) or Service User Number (SUN) (see the <a href="np_listcredscheme.html"> List Creditor Scheme</a> request)
* Reference an active mandate (its resource ID)
* A successful request will result in a Direct Debit being set up in `READY_FOR_EXPORT` [status](np_ddstatuses.html): the payment is created but has not yet been forwarded to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing</a> or to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.bacs-clearing}}">Bacs Clearing</a> for processing (see <a href ="np_ddstatuses.html">Direct Debit Statuses</a> for more information).

{% include tip.html content="Nuapay allows you to create a mandate/DDI and a Direct Debit payment in a single API request. For more details on this see the [Create Direct Debit and Mandate](np_createddandmand.html) request." %}

{% include idempotency.html %}

## A Note on Payment References in the Bacs Scheme

When creating a Direct Debit against a Bacs DDI, please note:

* Your payment must include a reference that includes your DDI (the Core Reference). Note that the reference you provide:
  * **IMPORTANT! Must include the `mandateId` i.e. the DDI reference as its initial characters**; so if your DDI Reference (`mandateId`) is ``ABCDEF123`` then valid reference values would be `ABCDEF123-01`, `ABCDEF12302`, `ABCDEF123/456`, for example. If required you may simply always provide the same reference:  ``ABCDEF123``.
  * Must be at least 6 alphanumeric characters in length and cannot exceed a total of 18 characters.
  * Cannot begin with `DDIC` (this is reserved for PSP use).
  * Should only be composed of upper-case characters.
  
* If you don't pass a reference, Nuapay will automatically generate one for you and store the DDI Reference as the `structuredRemittanceInformation.reference`. A unique `endToEndId` is also generated.
* If you you provide an `endToEndId` this will be saved as the `structuredRemittanceInformation.reference` subject to a duplicate check.
* If an `endToEndId` and a `structuredRemittanceInformation.reference` are provided in your request, the `structuredRemittanceInformation.reference` is used as the DDI (Core) Reference.
* If you only provide a `structuredRemittanceInformation.reference`, Nuapay will generate an `endToEndId` and the `structuredRemittanceInformation.reference` is used as the Core Reference.
* The following non-alphanumeric characters are supported and may be used in the `endToEndId` identifier:
  * Full stop(.)
  * Slash (/)
  * Hyphen (-)
  * Blank space ( )

{% include warning.html content="If you do not follow these rules for specifying the Payment Reference value, when the payment file is passed to the Bacs scheme for processing, your payer's bank will be unable to match the transaction to a DDI and your payment will be rejected." %}


{% include tip.html content="Payers will typically see your Service User Name and the Core Reference on their bank statements. Different banks have different standards however and while all will display your Service User Name, not all will display the Core Reference." %}


{% include swagger_np.html %}

{% include urls.html %}

{% include tip.html content="You must use the resource identifier of the `schemeId`/ `mandateId`/ `directDebitId` in your requests and not the actual creditor scheme ID/SUN or Unique Mandate Reference or Direct Debit identifier. Resource identifiers are short alphanumeric strings, similar to this: abxq9kq52l. Depending on the request you may need 1, 2 or all 3 of these resource identifiers in your URI." %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addSinglePaymentUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
