---
title: View Bank
keywords: View Banks Open Banking 
summary: "View Bank RESTful API"
sidebar: ob_sidebar
permalink: ob_viewbank.html
folder: prodOpenBanking
toc: false
---

## API Details

Pass a BankID to this endpoint to return details of a specific ASPSP.

{% include swagger_ob.html %}


{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getBankUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
