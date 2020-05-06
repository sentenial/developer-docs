---
title: Forward Payment Callback
keywords: Forward the Payment Callback to Nuapay TPP
summary: "Applicable for the SELF_HOSTED_CALLBACK integration only. Use this service to pass the Payment Callback to Nuapay TPP"
sidebar: ob_sidebar
permalink: ob_paymentcallback.html
folder: prodOpenBanking
toc: false
---

## API Details

{% include swagger_ob.html %}

{% include important.html content="This service is only required if you have chosen the **SELF_HOSTED_CALLBACK** integration model." %}

The Forward Payment Callback service allows you to pass the callback parameters received to the `merchantPostAuthUrl` to the Nuapay TPP. 



{% include urls-ob.html %}

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/forwardPaymentCallbackPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
