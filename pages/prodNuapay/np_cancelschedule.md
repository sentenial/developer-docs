---
title: Cancel Payment Schedule
keywords: sample
summary: "Cancel Payment Schedule RESTful API"
sidebar: np_sidebar
permalink: np_cancelschedule.html
folder: prodNuapay
toc: false
---

## API Details

In a Fixed-Length schedule the <b>Cancel Payment Schedule</b> request will set the status of any READY FOR EXPORT Direct Debit transactions in a payment schedule to REVOKED.

In an open-ended schedule the current READY FOR EXPORT payment is updated to Cancelled and no additional payments will be added.

{% include important.html content="Direct Debits that have been EXPORTED are unaffected by the cancel payment schedule request" %}

(See <a href="np_ddstatuses.html">Direct Debit Statuses</a> for more information on the various payment statuses that are possible).

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/cancelPaymentScheduleUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
