---
title: Retrieve Banks
keywords: Retrieve Banks Open Banking 
summary: "Retrieve Bank RESTful API - use this service to retrieve the list of participating banks"
sidebar: ob_sidebar
permalink: ob_getbank.html
folder: prodOpenBanking
toc: false
---

## API Details

The Retrieve Bank service allows you to retrieve a list of banks participating in Open Banking.
The participating ASPSPs are returned in order of popularity (dynamically determined based on Nuapay PSUs' preferences).

{% include tip.html content="Only one test bank (NUAPAY ASPSP OPENIDCONNECT) is available on the Sandbox environment." %}


{% include swagger_ob.html %}


{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getBanksUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
