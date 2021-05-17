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

The Retrieve Bank service allows you to: 
* Retrieve a list of the banks participating in Open Banking.
* Filter based on:
  * The `supportedcurrencies` of the bank.
  * The `country` in which the bank is based (using the ISO 3166 country code). 

The participating ASPSPs are returned in order of popularity (dynamically determined based on Nuapay PSUs' preferences).

{% include tip.html content="Only one test bank (NUAPAY ASPSP OPENIDCONNECT) is available on the Sandbox environment." %}

|Where you specify two or more value for the `supportedcurrencies` array (in the Query Parameters of your request), the ASPSPs returned will support either currency; so the parameter is treated as a logical OR (not as an AND).|


{% include swagger_ob.html %}


{% include urls-ob.html %}

## Retrieve Banks Endpoint

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
