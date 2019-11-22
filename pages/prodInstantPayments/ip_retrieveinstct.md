---
title: Retrieve Instant Payment
keywords: SEPA Instant CT Retrieve
summary: "Retrieve SCT Instant RESTful API"
sidebar: ip_sidebar
permalink: ip_retrieveinstct.html
folder: prodInstantPayments
toc: false
---


When an Instant Payment is created in the Origix IP system it is given a unique identifier (the URI). This identifier is returned in the response to the <a href ="ip_createinstct.html">Create Instant Payment</a> request.

The Retrieve Instant Payment request allows you to look up the details of a given payment. The payment's ID, end-to-end identifier, time stamp etc. are all returned.

You must provide the transaction's unique URI as a GET request:


## API Details

{% include swagger_ip.html %}

{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/instant-payments-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/GetInstantPaymentsUsingGET','#profileTabs',timerRef); }, 500);

</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}