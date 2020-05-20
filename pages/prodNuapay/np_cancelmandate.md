---
title: Cancel Mandate / DDI
keywords: sample
summary: "Cancel Mandate RESTful API"
sidebar: np_sidebar
permalink: np_cancelmandate.html
folder: prodNuapay
toc: false
---

## API Details

It is only possible to cancel a mandate/DDI that is in `ACTIVE` status. 

When you cancel a mandate/DDI:

* Any `READY FOR EXPORT` Direct Debit transactions linked to it are automatically cancelled.
* No further collections may be made against the mandate/DDI.

If you want to engage with your payer at a later point, and want to collect direct debit payments once again, you will need to create a new mandate/DDI.


{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/cancelMandateUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
