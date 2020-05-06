---
title: Retrieve Refund
keywords: Single Refund View an Open Banking Payment
summary: "View a specific refund linked to an Open Banking Payment RESTful API"
sidebar: ob_sidebar
permalink: ob_refundpaymentview.html
folder: prodOpenBanking
toc: false
---

## API Details

{% include swagger_ob.html %}

The View Refund Payment service allows you to view the details of a single `refundId` linked to a `paymentId`. Use [List Refund Payments](ob_refundpaymentlist.html) to retrieve one a `refundId` linked to a payment.

{% include urls-ob.html %}

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getRefundUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
