---
title: Retrieve Banks
keywords: Retrieve Banks Open Banking 
summary: "Retrieve Bank RESTful API"
sidebar: ob_sidebar
permalink: ob_getbank.html
folder: prodOpenBanking
toc: false
---

## API Details

Before you can initiate an account access request to your customer you must first offer the customer a choice of available banks. This service allows you to retrieve a list of banks participating in Open Banking.


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
