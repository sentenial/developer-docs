---
title: List Accounts
keywords: List Accounts
summary: "List Accounts once you have retrieved an Active consent"
sidebar: ob_sidebar
permalink: ob_listaccount.html
folder: prodOpenBanking
toc: true
---

## API Details

This endpoint allows you to retrieve account details.


## List Accounts Endpoint


{% include swagger_ob_ais.html %}

{% include urls-ob.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger-ais/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listPSUAccountsUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
