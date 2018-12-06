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

{% include tip.html content="We recommend that you use a unique idempotency key with each unique Create Open Banking Payment request. The **x-idempotency-key** is a Header parameter in this API." %}


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
