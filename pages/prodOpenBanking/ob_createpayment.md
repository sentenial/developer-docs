---
title: Create Payment
keywords: Create Open Banking Payment
summary: "Create Open Banking Payment RESTful API"
sidebar: ob_sidebar
permalink: ob_createpayment.html
folder: prodOpenBanking
toc: false
---

## API Details 

The Create Payment service generates an Open Banking payment object, returning a unique ``paymentId`` with an (initial) status of  ``PENDING_APPROVAL``.

{% include swagger_ob.html %}


{% include tip.html content="We recommend that you use a unique idempotency key with each unique Create Open Banking Payment request. The **x-idempotency-key** is a Header parameter in this API." %}

## Providing the Debtor Account

In some cases you may already have a debtor account stored for a specific customer and you may want that user to use this account for the payment. 

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
