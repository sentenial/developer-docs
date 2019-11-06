---
title: SMS Authentication Conversation Step - Initialization
keywords: E-Mandate Conversation - Initialize
summary: "Once your configuration is correct, the GET Initialization step is the starting point in the conversation and also allows you to determine at what point you are in the flow (conversation) and what are the next availabe actions."
sidebar: em_sidebar
permalink: em_conversation_init.html
folder: prodEmandates
simple_map: true
map_name: usermap
box_number: 2
---

In this example conversation, we are setting up an e-mandate where the authorization method is **SMS**: 

* We have confirmed in the [previous step](em_conversation_settings.html) that the configuration is correct. 
* The response to the GET `/conversations/init` will indicate that the next available step (as indicated in the `views` object). 


{% include note.html content="This service may be called at any point and will always indicate where you are in the flow and what are the next possible steps." %}

Move to the next step of the conversation: [Sign](em_conversation_sign.html)

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
