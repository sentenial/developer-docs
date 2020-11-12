---
title: Create Credit Transfer
keywords: Create Credit Transfer
summary: "Create Credit Transfer RESTful API"
sidebar: np_sidebar
permalink: np_createdct.html
folder: prodNuapay
toc: false
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %} 


{% include tip.html content="Before you can generate a Credit Transfer (CT) payment, using this API request, you must first [Create a Beneficiary](np_createbeneficiary.html). Alternatively you can use the [Create Credit Transfer & Beneficiary](np_createctandbene.html) to create the payee and the payment in one API request." %} 

## SEPA Credit Transfers

When creating a SEPA Credit Transfer (also referred to as an SCT or CT) payments, note that:

* Payments are processed for **EUR currency payments only**
* CT payments, unlike Direct Debit payments, do not require that the transaction is passed to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing system</a> days in advance of the collection date.
* If you create your CT payment early enough on a specific working day (before 9 AM GMT), the funds will typically be credited to your beneficiary on the same day. 
* If you create the payment later in the day then the CT will generally be credited to the beneficiary on the following business day.

## Faster Payments

The Faster Payments Scheme (FPS) is an instant payment scheme (with funds being credited to the beneficiary generally in a matter of seconds) available in the UK.
Note that FPS:

* Is available for **GBP curency payments only**.   
* Unlike SEPA CT, FPS is a 24/7/365 system.
* Requires the following values in your request:
  * `paymentCurrency` = GBP.
  * `type` = EXPRESS

## Payment Types

Payments can have a `type`:

* STANDARD
* EXPRESS
* FASTEST_POSSIBLE

|**Currency**|**Default Type**|**CT Type**|
|EUR|`STANDARD`| SCT |
|EUR|`EXPRESS` | SCT Instant|
|GBP|`STANDARD`| Bacs Direct Credit|
|GBP|`EXPRESS`| FPS|

By default EUR payments are processed as `STANDARD`; GBP payments are processed as `EXPRESS`.

{% include tip.html content="If you would like a different default configuration, please discuss your requirements with your account manager." %}

Where you specify `FASTEST_POSSIBLE` a payment will go via the the Express payment if possible (i.e. if configured for you); if it is not possible to send the payment as Express  then the transaction will be processed as a Standard payment.


{% include note.html content="If you have 2 or more Nuapay accounts configured and want to transfer funds between these accounts you will need to use the [Transfer Between Accounts](np_accounttransfer.html) service" %}


{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addCreditTransferUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>



{% include links.html %}
