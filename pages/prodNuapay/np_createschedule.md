---
title: Create Payment Schedule
keywords: Create Payment Schedule
summary: "Create Payment Schedule RESTful API"
sidebar: np_sidebar
permalink: np_createschedule.html
folder: prodNuapay
toc: false
---

## API Details

The Create Payment Schedule request allows you to create either a Fixed-Length or an Open-Ended schedule. 

The fixed-length schedule will result in a number of Direct Debit payments being created; an open-ended schedule will generate a single Direct Debit (with additional single payments being added as required, based on the configured frequency of the payments).

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addPaymentScheduleUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
