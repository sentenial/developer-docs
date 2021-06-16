---
title: Retrieve E-Mandate Configuration 
keywords: Retrieve E-Mandate Configuration
summary: "Retrieve your E-Mandate application settings - use this service to view your current E-Mandate configurations settings."
sidebar: em_sidebar
permalink: em_retrieveconfig.html
folder: prodEmandates
---

As outlined in [E-Mandate Customisations](em_uicustomisations.html), it is possible to customise various setting in the E-Mandate application. 

Use this API to retrieve the details of your current configuration.

{% include swagger_em.html %}


{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 
 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/retrieveConfigUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>




{% include links.html %}
