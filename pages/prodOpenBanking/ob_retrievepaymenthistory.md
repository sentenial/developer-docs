---
title: Retrieve Payment History
keywords: Retrieve Open Banking Payment History
summary: "Retrieve Open Banking Payment History RESTful API"
sidebar: ob_sidebar
permalink: ob_retrievepaymenthistory.html
folder: prodOpenBanking
toc: false
---

## API Details

The Retrieve Payment History service allows you to view the history of a given `paymentId`. The service returns an array of events and datetimes. Viewing the payment history allows you to determine when a payment moved through its various [payment statuses](ob_paymentstatuses.html).    


{% include swagger_ob.html %}

{% include urls-ob.html %}

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 
loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getPaymentHistoryUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
