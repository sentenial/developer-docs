---
title: Retry Payment
keywords: Retry an Open Banking Payment
summary: "Retry Open Banking Payment RESTful API"
sidebar: ob_sidebar
permalink: ob_retrypayment_new.html
folder: prodOpenBanking
toc: true
---

## API Details 

The Retry Payment service allows you to re-try a payment that is in a non-final status: 

Note that:
 
* The payment must be in an appropriate "retry-able" status.
* The request must be made within the configured timeout period (default is 15 minutes).
* You must pass the original `paymentId` and the required `bankId`.

{% include tip.html content="This service is only required for `SELF-HOSTED` and `SELF-HOSTED-CALLBACK` integrations; for `CHECKOUT` and `REDIRECT` users, the logic for handling retries is built into the Nuapay TPP user unterface." %}

See [Payment Retries](ob_paymentretries.html) for more details.

{% include swagger_ob.html %}

{% include urls-ob.html %}

## Retry Payment Endpoint


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoctest.html');
var timerRef = setInterval(function() { getDocs('operation/setBankIdForPaymentUsingPATCH','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
