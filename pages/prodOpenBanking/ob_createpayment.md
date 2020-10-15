---
title: Create Payment
keywords: Create Open Banking Payment
summary: "Create Open Banking Payment RESTful API"
sidebar: ob_sidebar
permalink: ob_createpayment.html
folder: prodOpenBanking
toc: true
---

## API Details 

The Create Payment service generates an Open Banking payment object, returning a unique ``paymentId`` with an (initial) status of `PENDING` (in Checkout Mode) or `PENDING_APPROVAL` (in Self-Hosted and Self-Hosted-Callback modes). See [PISP Implementation Options](ob_pispimplementations.html) for more on the available modes.

{% include swagger_ob.html %}


## Idempotency in Payment Requests

{% include tip.html content="We recommend that you use a unique idempotency key with each unique Create Open Banking Payment request. The **Idempotency-Key** is a Header parameter in this API." %}


The Idempotency check is only against successful payments, so where a previous payment request has resulted in any of the following [HTTP Response Codes](ob_httpreasons.html), that Idempotency key may be reused without any issue:`401`, `403`, `404`, `408`, `500`, `501`, `503`


## Providing a Payment Reference

You have the option to provide your own identifier to your transactions (the default) or, if you would prefer, a unique system-generated identifier may be automatically applied. 

If your configuration requires that merchant-generated references must be provided, please note that:

* For GB payments `remittanceInformation.refererence` must be a maximum of 18 characters
* For non-GB payments 35 characters are allowed.

Payment identifiers have two attributes:

* The reference itself
* The reference’s time to live (default is 3 days)

The reference must be unique per merchant account within the defined time to live. If you require a variation on the default time-to-live setting of 3 days, please contact your account manager who will update your configuration as required.

Where you reuse a reference, which was linked to a previously generated payment, and it is referenced within the time-to-live limit, your request will result in a `422` response: Duplicate Reference provided.

## Providing the Debtor Account

**Berlin Group - NextGenPSD2 XS2A Specification**

If you are processing payments under the Berlin Group NextGenPSD2 specification `debtorAccount` is mandatory and must be provided as an IBAN. 

**Open Banking UK - OBIE Specification**

While providing the `debtorAccount` is not mandatory for OBUK, in some cases you may already have a debtor account stored for a specific customer and you may want that user to use that account for the payment. 

The `/payments` service allows you to provide the PSU account information as an IBAN or as a Sort Code and Account number (for GB accounts in UK Open Banking).

The `schemeName` under the `debtorAccount`object, can be provided in two ways, as:

* `IBAN`
* `SortCodeAccountNumber`

Where `IBAN` is used the PSU's IBAN is provided for `identification`:

<pre>
<code class="json">
"debtorAccount": {
   "identification": "GB34BARC20051122334455",
   "schemeName": "IBAN"
}
</code>
</pre>

Where `SortCodeAccountNumber` is used the Sort Code and Account number are concatenated and provided for `identification`. 

Example: Sort Code = 12-34-56 & Account = 87654321 gives:

<pre>
<code class="json">
"debtorAccount": {
   "identification": "12345687654321",
   "schemeName": "SortCodeAccountNumber"
}
</code>
</pre>

If you do not specify an account in this request, and assuming the PSU has more than one account, the ASPSP will typically allow the user to select any of his/her accounts for the payment, via a drop-down. 



{% include urls-ob.html %}

## Create Payment Endpoint


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/createPaymentUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
