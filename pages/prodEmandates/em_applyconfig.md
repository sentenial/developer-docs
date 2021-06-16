---
title: Apply E-Mandate Configuration 
keywords: Apply E-Mandate Configuration
summary: "Configure the E-Mandate application settings - specify the colours required to match your branding and/or set your company icon, which will be displayed on the E-Mandate UI and in email notifications, etc."
sidebar: em_sidebar
permalink: em_applyconfig.html
folder: prodEmandates
---

As outlined in [E-Mandate Customisations](em_uicustomisations.html), it is possible to customise various setting in the E-Mandate application. 

This API allows you to configure your required customisations.

{% include swagger_em.html %}


{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 
 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/updateConfigUsingPUT','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>




{% include links.html %}
