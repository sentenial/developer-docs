---
title: Retrieve Mandate / DDI
keywords: Retrieve Mandate API
summary: "Retrieve Mandate RESTful API"
sidebar: np_sidebar
permalink: np_retrievemandate.html
folder: prodNuapay
toc: false
---

## API Details

Note that:

* The Retrieve Mandate endpoint allows you to view the details of a specific mandate/DDI stored in Nuapay.
* The request requires that you provide the Mandate/DDI resource identifier (as returned in the [Create Mandate](np_createmandate.html) call service): the `mandateId`.

{% include swagger_np.html %}

{% include urls.html %}
{% include tip.html content="You must use the resource identifier of the `schemeId` in your request and not the actual creditor scheme ID or SUN. This identifier will be similar to this: abxq9kq52l. Similarly, the mandate identifier is the resource identifier (e.g., rtsxq8kaby5) and is not the actual unique mandate reference - so in this case you would call GET /schemes/abxq9kq52l/mandates/rtsxq8kaby5" %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/viewMandateUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
