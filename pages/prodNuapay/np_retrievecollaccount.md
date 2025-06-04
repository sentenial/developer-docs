---
title: List Collective Accounts
keywords: List Collective Accounts
summary: "List Collective Account RESTful API"
sidebar: acc_sidebar
permalink: np_retrievecollaccount.html
folder: prodNuapay
toc: true
---

## API Details

Use this service to retrieve the full set of Collective Accounts that you have configured.

{% include swagger_pa.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/posting-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listCollectiveAccountUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
