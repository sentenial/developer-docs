---
title: Retrieve Conversation Settings 
keywords: Retrieve Conversation Settings
summary: "The Retrieve Conversation Settings API returns configuration details and indicates the next steps in the current conversation."
sidebar: em_sidebar
permalink: em_retrsettings.html
folder: prodEmandates
---

The Retrieve Conversation Settings services:

* Returns configuration details.
* Indicates what conversation step is available (via `views`)

In order to call this API you must: 
* First retrieve an E-Mandate Token (see [Prepare E-Mandate](em_prepare.html))
* Reference this token as a HTTP header parameter.


{% include swagger_em.html %}


{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 
 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/settingsGetUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>




{% include links.html %}
