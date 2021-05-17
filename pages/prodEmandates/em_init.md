---
title: Initialize Conversation 
keywords: Initialize Conversation
summary: "The Initialize Conversation API allows you to determine where you are in the current conversation and what are the next available steps."
sidebar: em_sidebar
permalink: em_init.html
folder: prodEmandates
---

The Initialize Conversation API:

* May be called at any point in the E-Mandate Conversation.
* Indicates the next available conversation step(s) (via the `views` object).


{% include swagger_em.html %}


{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 
 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/initGetUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>




{% include links.html %}
