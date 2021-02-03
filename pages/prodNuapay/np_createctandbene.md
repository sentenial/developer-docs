---
title: Create Credit Transfer & Beneficiary
keywords: Create Credit Transfer & Beneficiary
summary: "Create Credit Transfer & Beneficiary RESTful API - generate a payment and its beneficiary in a single API call."
sidebar: np_sidebar
permalink: np_createctandbene.html
folder: prodNuapay
toc: false
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %} 

The Create Credit Transfer request requires that you have first created a beneficiary. In some scenarios it is simpler to generate both the beneficiary and the payment at the same time and this request allows you to do that. 

{% include note.html content="If the beneficiary details you reference in the request have been previously provided (and that beneficiary is already stored against your merchant profile) Nuapay will reuse that stored beneficiary data: a new beneficiary is only created if his/her beneficiary account has not been referenced before in a previous Credit Transfer payment." %}

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
  
{% include tip.html content="If you specify domestic account details for the beneficiary account, specify the Sort Code in **domesticBranchCode** (not in the **domesticBankCode**)." %}

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


{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addCTBeneficiaryOnFlyUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>



{% include links.html %}
