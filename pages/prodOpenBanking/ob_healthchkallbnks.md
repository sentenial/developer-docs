---
title: Health Check - All Banks
keywords: Health Check all banks
summary: "Perform a health check on all ASPSPs via RESTful API"
sidebar: ob_sidebar
permalink: ob_healthchkallbnks.html
folder: prodOpenBanking
toc: true
---

## API Details 

The Health Check service for all banks returns a score for all APSPs.

* Possible Scores: 
  * `0`: There are some connectivity issues. 
  * `100`: The ASPSP is available. 
  * `-1`: The service is not supported by the ASPSP. 


{% include urls-ob.html %}

## Health Check (All ASPSPs) Endpoint


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/health-status-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getBanksStatusUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
