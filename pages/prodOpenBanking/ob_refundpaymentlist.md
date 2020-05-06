---
title: List Refund Payments
keywords: List Refunds an Open Banking Payment
summary: "List the refund(s) linked to an Open Banking Payment RESTful API"
sidebar: ob_sidebar
permalink: ob_refundpaymentlist.html
folder: prodOpenBanking
toc: false
---

## API Details

{% include swagger_ob.html %}

The List Refund Payment service allows you to retrieve a list of refunds linked to a single `paymentId`. A single payment may have one or more refunds linked to it.



{% include urls-ob.html %}

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listRefundsUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
