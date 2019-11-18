---
title: List Account Balances
keywords: List Account Balances API
summary: "List Account Balances RESTful API"
sidebar: np_sidebar
permalink: np_listaccountbals.html
folder: prodNuapay
toc: false
---

## API Details

Use this request to return the balance on a specific account.

{% include note.html content="This request uses the `dateuntil` parameter. This takes a Unix Epoch timestamp and defaults to the current date" %}

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/viewAccountBalancesUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
