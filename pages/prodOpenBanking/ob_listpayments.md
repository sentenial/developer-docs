---
title: List Payments
keywords: List Open Banking Payment
summary: "List Open Banking Payments RESTful API"
sidebar: ob_sidebar
permalink: ob_listpayments.html
folder: prodOpenBanking
toc: false
---

## API Details

The List Payments service returns a list of Open Banking payments. Filter the list returned by specifying a `fromDateTime` and a `toDateTime` or by poassing a specific `paymentStatus`, for example.

{% include swagger_ob.html %}

{% include urls-ob.html %}

## List Payments Endpoint

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 
loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getPaymentListUsingGet','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
