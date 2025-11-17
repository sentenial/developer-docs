---
title: List Account Settlements
keywords: List Account Settlements
summary: "List Account Settlements RESTful API"
sidebar: acc_sidebar
permalink: np_listaccountsetmts.html
folder: prodNuapay
toc: true
---

## API Details

Use this service to retrieve the full set of the settlements made against the provided account.
You will need to provide your `accountId`. Contact your Account Manager or the Support team if you do not have this value.

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listSettlementsUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
