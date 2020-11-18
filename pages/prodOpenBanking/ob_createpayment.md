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

The Create Payment service: 
* Generates an Open Banking payment object. 
* Returns a unique ``paymentId`` with an (initial) [status](ob_paymentstatuses.html) of `PENDING` (in Checkout and Redirect Mode) or `PENDING_APPROVAL` (in Self-Hosted and Self-Hosted-Callback modes). 
* See [PISP Implementation Options](ob_pispimplementations.html) for more on the available modes.

{% include swagger_ob.html %}


## Idempotency in Payment Requests

{% include tip.html content="We recommend that you use a unique idempotency key with each unique Create Open Banking Payment request. The **Idempotency-Key** is a Header parameter in this API." %}


The Idempotency check is only against successful payments, so where a previous payment request has resulted in any of the following [HTTP Response Codes](ob_httpreasons.html), that Idempotency key may be reused without any issue:

* `401`
* `403`
* `404`
* `408`
* `500`
* `501`
* `503`

## Remittance Reference

You have the option to provide your own remittance reference to your transactions (the default) or, if you would prefer, a unique system-generated remittance reference may be automatically applied. This reference unambiguously refers to the payment transaction.

If your configuration requires that merchant-generated references must be provided, please note that:

* For GB payments `remittanceInformation.refererence` must be a maximum of 18 characters
* For non-GB payments, 35 characters are allowed.

Payment identifiers have two attributes:

* The reference itself
* The reference’s time to live (default is 3 days)

Note that:

* The reference must be unique per merchant account within the defined time to live. 
* If you require a variation on the default time-to-live setting of 3 days, please contact your account manager who will update your configuration as required.
* Where you reuse a reference, which was linked to a previously generated payment, and it is referenced within the time-to-live limit, your request will result in a:
  * `422` response: Duplicate Reference provided.

## End-to-End Identifiers

If you want to provide an `endToEndIdentification` note that for:

* EUR currency transactions, the max length allowable is 35 characters.
* GBP currency transactions allow a max length of 31 characters.

## The Debtor Account

Handling of the Debtor Account varies based on the Open Banking Scheme: 

|**Berlin Group**|If you are processing payments under the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.berlin-group}}">Berlin Group</a> NextGenPSD2 specification `debtorAccount` **is mandatory** and must be provided as an IBAN.|
|**Open Banking UK**|While providing the `debtorAccount` is not mandatory for <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.obie}}">OBUK</a>, in some cases you may already have a debtor account stored for a specific customer and you may want that <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> to use that account for the payment.| 

The `/payments` service allows you to provide the PSU account information (i.e. the `debtorAccount`) as an IBAN or as a Sort Code and Account number (for GB accounts).

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

Example: Sort Code = `12-34-56` & Account = `87654321` gives:

<pre>
<code class="json">
"debtorAccount": {
   "identification": "12345687654321",
   "schemeName": "SortCodeAccountNumber"
}
</code>
</pre>

If you do not specify an account in this request, and assuming the PSU has more than one account, the ASPSP will typically allow the user to select any of his/her accounts for the payment, via a drop-down. 

## Address Details

{% include tip.html content="Debtor address is only required in the **STET** Scheme." %}

In STET:
* Certain STET ASPSPs require that you provide the debtor address in your payment request. 
* It is also possible to pass the merchant (creditor) address in your request if required. 
* If no creditor address details are provided, but are required for the selected ASPSP, the Nuapay TPP will pass the address stored against the merchant's profile.


## Setting an Execution Date

{% include tip.html content="It is only possible to specify a future-dated payment in the **STET** Scheme." %}

Use `requestedExecutionDate` if you want to specify a future-dated payment. 

Note that:

* The payment must be initiated against a <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.stet}}">STET</a>-supporting ASPSP.
* The payment can have a date up to 30 days into the future.
* The date cannot be in the past; if a past date is provided a `T0058` error is triggered: "Requested Execution Date cannot be post cut-off time or in the past."
* The Requested date specified may be a non-processing date (a holiday or weekend); the TPP does not validate this.
* Dates must be passed as YYYY-MM-DD.

|If a future-dated payment is specified in the payment request for a payment linked to an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.obie}}">OBUK</a> or to a <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.berlin-group}}">Berlin Group</a> ASPSP it will be rejected.|


## Creditor Accounts

In some cases you might want to specify the creditor/beneficiary account (i.e. your merchant account) into which funds will be credited following a successful payment. 

You can provide your creditor account information: 

* As an IBAN
  
  OR

* as a Sort Code and Account number (for GB accounts in UK Open Banking).

To do this use the `schemeName` under the `creditorAccount`object as one of the following:

* `IBAN`
* `SortCodeAccountNumber`

Where `IBAN` is used your creditor's IBAN is provided for `identification`:

<pre>
<code class="json">
"creditorAccount": {
   "identification": "GB34BARC20051122334455",
   "schemeName": "IBAN"
}
</code>
</pre>

Where `SortCodeAccountNumber` is used the Sort Code and Account number are concatenated and provided for `identification`. 

Example: Sort Code = `12-34-56` & Account = `87654321` gives:

<pre>
<code class="json">
"creditorAccount": {
   "identification": "12345687654321",
   "schemeName": "SortCodeAccountNumber"
}
</code>
</pre>

Note that:

**For GB Payments**:

1. The only allowed account country format is GB.
1. UK Faster Payments is the only allowed payment scheme.
1. The account format is sort code and account number.

**For EUR payments**: 

1. IBAN is the only allowed account format.
1. SEPA Credit Transfer and SEPA Instant Credit Transfer are allowed payment schemes.
1. The Payment Scheme corresponds to the currently available Local Instrument/ Payment Type configuration at API level and ASPSP level. Merchant requests that contains a payment scheme that is different to the scheme set at the ASPSP level will be rejected.
1. Creditor Account `IBAN`/`sortCodeAccountNumber` validations in terms of account validity are the same as for `debtorAccount`.


{% include tip.html content="If you do not specify a creditor account then the payment will be processed as per the configured defaults for your merchant." %}


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
