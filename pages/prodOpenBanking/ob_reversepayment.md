---
title: Reverse Payment
keywords: Reverse Open Banking Payment
summary: "Reverse an Open Banking Payment RESTful API"
sidebar: ob_sidebar
permalink: ob_reversepayment.html
folder: prodOpenBanking
toc: false
---

## API Details

The Reverse Payment service allows you to reverse/refund an Open Banking payment. 

{% include important.html content="Reversing a payment is only possible if you are using a Nuapay account as your merchant account; if your Open Banking payments have not been credited to this account then the Nuapay system has no beneficiary account reference and cannot reverse the funds to the appropriate customer account. " %}

A successful request will put the payment into REVERSE_REQUESTED status. The payment will be automatically debited from your Nuapay account and credited to your customer's account. 

Once the payment is successfully refunded (with funds disbursed to your customer's account) a Webhook notification will be fired to your configured Webhooks Endpoint. See <a href="ob_whrreversed.html">Payment Reversed</a> in the Webhooks section for more details.

{% include note.html content="Depending on the payment scheme you are using reversed payments may be settled the following business day e.g. for SEPA CTs or funds may be credited in a matter of seconds via the SEPA CT Instant Scheme or via Faster Payments in the UK." %}


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
