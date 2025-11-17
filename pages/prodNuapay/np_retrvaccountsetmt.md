---
title: Retrieve Account Settlement
keywords: Retrieve Account Settlement
summary: "Retrieve Account Settlement RESTful API"
sidebar: acc_sidebar
permalink: np_retraccountssetmt.html
folder: prodNuapay
toc: true
---

## API Details

Use this service to retrieve the details of a specific settlement. (Call [List Account Settlements](np_listaccountsetmts.html) initially to retrieve the required `settlementId`).

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/retrieveSettlementUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
