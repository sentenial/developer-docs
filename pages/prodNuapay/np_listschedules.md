---
title: List Payment Schedules
keywords: List Payment Schedules API
summary: "List Payment Schedules RESTful API"
sidebar: np_sidebar
permalink: np_listschedules.html
folder: prodNuapay
toc: true
---

## API Details

The List Payment Schedule request allows you to view a collection of payment schedules linked to:

* A Mandate
* A Specific Scheme
* All schemes (i.e. all schedules)

Use an appropriate URI (as described below) to return the required collection of Payment Schedules.

{% include swagger_np.html %}

{% include urls.html %}

## Lists Schedules Linked to a Mandate

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listPaymentSchedulesMandateUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

## Lists Schedules Linked to a Scheme

<ul id="profileTabs2" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef2 = setInterval(function() { getDocs('operation/listPaymentSchedulesSchemeUsingGET','#profileTabs2',timerRef2); }, 500);
</script>
</div>
</div>


## Lists all Schedules (linked to the Originator)


<ul id="profileTabs3" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}

var timerRef3 = setInterval(function() { getDocs('operation/listPaymentSchedulesOrganizationUsingGET','#profileTabs3',timerRef3); }, 500);
</script>
</div>
</div>

{% include links.html %}
