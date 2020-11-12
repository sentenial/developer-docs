---
title: Health Check - Single Bank
keywords: Health Check single bank
summary: "Perform a health check on a specific ASPSP to retrive its score"
sidebar: ob_sidebar
permalink: ob_healthchkbnk.html
folder: prodOpenBanking
toc: true
---

## API Details 

The Health Check service for a single bank returns a score for that specific ASPSP. 

* You must provide the required `{bankId}`.
* Possible Scores: 
  * `0`: There are some connectivity issues. 
  * `100`: The ASPSP is available. 
  * `-1`: The service is not supported by the ASPSP. 

Use the [Retrieve Banks](ob_getbank.html) service to retrieve a specific `bankId`.

{% include swagger_hc.html %}

{% include urls-ob.html %}

## Health Check (Single ASPSP) Endpoint


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/health-status-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getBankStatusUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
