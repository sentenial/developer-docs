---
title: Cancel Mandate
keywords: sample
summary: "Cancel Mandate RESTful API"
sidebar: np_sidebar
permalink: np_cancelmandate.html
folder: prodNuapay
toc: false
---

## API Details

<p>When you cancel a mandate:</p>

* Any READY FOR EXPORT transactions linked to it are automatically cancelled.
* No further collections may be made against the mandate.

<p>If you want to engage with your payer at a later point and want to take direct debit payments, you will need to create a new mandate.</p>


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
