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

* A Mandate/DDI
* A Specific Scheme
* All schemes (i.e. all schedules)

Use an appropriate URI (as described below) to return the required collection of Payment Schedules.

{% include swagger_np.html %}

{% include urls.html %}

{% include tip.html content="You must use the resource identifier of the `schemeId`/ `mandateId`/ `paymentScheduleId` in your requests and not the actual creditor scheme ID/SUN or Unique Mandate Reference or payment schedule identifier. Resource identifiers are short alphanumeric strings, similar to this: abxq9kq52l. Depending on the request you may need 1, 2 or all 3 of these resource identifiers in your URI." %}


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
