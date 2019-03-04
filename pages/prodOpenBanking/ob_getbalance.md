---
title: Retrieve Account Balance
keywords: Retrieve Account Balance Open Banking 
summary: "Retrieve Account Balance RESTful API"
sidebar: ob_sidebar
permalink: ob_getbalance.html
folder: prodOpenBanking
toc: false
---

## API Details

Return the current balance on a specified account.

{% include swagger_ob.html %}

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getAccountBalancesUsingGET','#profileTabs',timerRef); }, 500);

</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}