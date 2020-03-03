---
title: Refund Payment
keywords: Refund an Open Banking Payment
summary: "Refund an Open Banking Payment RESTful API"
sidebar: ob_sidebar
permalink: ob_refundpayment.html
folder: prodOpenBanking
toc: false
---

## API Details

The Refund Payment service allows you to refund an Open Banking payment. 

{% include important.html content="Refunding a payment is only possible if you are using a Nuapay account as your merchant account; if your Open Banking payments have not been credited to this account then the Nuapay system has no beneficiary account reference and cannot refund the funds to the appropriate customer account. " %}

When you initiate a refund request, a new refund object is created. 

The refund request object may be in one of three statuses:

* REFUND_PENDING
* REFUND_COMPLETE
* REFUND_REJECTED

Where a refund request is successful:

1. The user calls the `/payments/{paymentId}/refunds` service. Provided the referenced payment is in `PAYMENT_RECEIVED` status (and all other [Refund Configuration](ob_refundpayment.html#refund-configuration) constraints are met), a **refund object** is created in `REFUND_PENDING` status. Note that the actual payment status is unchanged.
1. A Credit Transfer payment is initiated to the customer account linked to the provided `paymentId`.
1. The payment is successfully processed - funds are credited to the PSU. The refund object's status is updated to `REFUND_COMPLETE`
1. A Payment Refund Complete Webhook notifies the merchant of the successful refund. See <a href="ob_whrefundcomplete.html">Payment Refunded Event</a> in the Webhooks section for more details.

Where a refund request is unsuccessful:

1. The user calls the `/payments/{paymentId}/refunds` service and all validations (as mentioned above) are passed.
1. A Credit Transfer payment is initiated to the customer account linked to the provided `paymentId` but cannot be processed e.g. the PSU's account is closed.
1. The refund object is updated to `REFUND_REFJECTED` 

{% include note.html content="Where a refund is unsuccessful you will not be notified via a Webhook; instead you would need to use the Retrieve Payment service (passing the refund object identifier) to determine the refund status. A Webhook will be available for this in the next Open Banking release." %}

## Refund Options

It is possible to issue a refund for:

* The full amount of the initial transaction (a full refund)
* An amount that is less than the original transaction (a partial refund)
* The full amount & a compensation amount (a full refund and compensation)

The value of your refund is handled in the API via the `refundAmount` and `compensatioinAmount` values.

## Refund Configuration

To allow merchants to manage the refund process, it is possible to apply limits on the value of refunds. 
The following settings may all be configured per merchant; please discuss your requirements with your Account Manager:

|**Setting**|**Description**|**Default**|
|Refund Amount Limit per Payment| The maximum amount that can be refunded against a payment. The sum of all refunds against a single payment cannot exceed this number|0|
|Maximum Refund Percentage per Transaction|Percentage of the original transaction amount that can be Refunded in a single refund (whole numbers only, no decimal places, e.g. 1% is acceptable, 0.1% is not)|0|
|Refunds Period|The maximum Refund period in days; it is not possible to initiate a refund for a payment that is older than this configured number of days.|540|

These configurations are evaluated when you make a refund request. 

A refund will be initiated where:

* The payment you want to refund is in `PAYMENT_RECEIVED` status.
* The refund amount does not exceed:
  * The (global) maximum refund amount
  * The refund transaction amount limit.
* The refund occurs within the defined refunds period.



{% include note.html content="Depending on the payment scheme you are using, reversed payments may be settled the following business day e.g. for SEPA CTs or funds may be credited in a matter of seconds via the SEPA CT Instant Scheme or via Faster Payments in the UK." %}


{% include swagger_ob.html %}


{% include urls-ob.html %}

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/reversePaymentUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
