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

Before you can generate a Credit Transfer (CT) payment, using this API request, you must have first <a href = "np_createbeneficiary.html">created a beneficiary</a>.

## SEPA Credit Transfers
CT payments, unlike Direct Debit payments, do not require that the transaction is passed to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing system</a> days in advance of the collection date.

If you create your CT payment early enough on a specific working day, the funds could be credited to your beneficiary on the same day. If you create the payment later in the day then the CT will generally be credited to the beneficiary on the following business day.

## Faster Payments
GPB curency Credit Transfer payments are processed through the Faster Payments Scheme (FPS). FPS are instant payments with funds being credited to the beneficiary generally in a matter of seconds. 
To generate an FPS payment ensure that you provide the following in your request:

1. `paymentCurrency` = GBP.
1. `type` = EXPRESS


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
