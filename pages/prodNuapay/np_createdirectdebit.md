---
title: Create Direct Debit
keywords: Create Direct Debit
summary: "Create Direct Debit RESTful API"
sidebar: np_sidebar
permalink: np_createdirectdebit.html
folder: prodNuapay
toc: false
---

## API Details

The Create Direct Debit request must:

* Include the resource identifier Creditor Scheme ID (CSID) or Service User Number (SUN) (see the <a href="np_listcredscheme.html"> List Creditor Scheme</a> request)
* Reference an active mandate (its resource ID)
* A successful request will result in a Direct Debit being set up in `READY_FOR_EXPORT` [status](np_ddstatuses.html): the payment is created but has not yet been forwarded to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing</a> or to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.bacs-clearing}}">Bacs Clearing</a> for processing (see <a href ="np_ddstatuses.html">Direct Debit Statuses</a> for more information).

{% include tip.html content="Nuapay allows you to create a mandate/DDI and a Direct Debit payment in a single API request. For more details on this see the [Create Direct Debit and Mandate](np_createddandmand.html) request." %}

{% include idempotency.html %}

## A Note on End-to-End Identifiers in the Bacs Scheme

When creating a Direct Debit against a Bacs DDI, please note:

* The `endToEndId` will be automatically applied if you do not want to provide this identifier.
* If you do want to specify the `endToEndId` it must follow the following rules:
  * It must be at least 6 alphanumeric characters in length and cannot exceed a total of 18 characters.
  * **IMPORTANT! It must include the `mandateId` i.e. the DDI reference as its initial characters**; so if your `mandateId` is ``ABCDEF123`` then valid `endToEndId` values would be `ABCDEF123-01`, `ABCDEF12302`, `ABCDEF123/456`, for example.
* The following non-alphanumeric characters are supported and may be used in the `endToEndId` identifier:
  * Full stop(.)
  * Slash (/)
  * Hyphen (-)
  * Blank space ( )

{% include warning.html content="If you do not follow these rules for specifying the End-to-End value, when the payment file is passed to the Bacs scheme for processing, your payer's bank will be unable to match the transaction to a DDI and your payment will be rejected." %}

{% include swagger_np.html %}

{% include urls.html %}


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
