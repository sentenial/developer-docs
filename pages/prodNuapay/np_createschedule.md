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

The Create Payment Schedule request allows you to create either a <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.schedule-fixed}}">Fixed-Length</a> or an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.schedule-open}}">Open-Ended</a> schedule. 

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
