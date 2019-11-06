---
title: SMS Authentication Conversation Step - Verify
keywords: E-Mandate Conversation - Verify
summary: "After completing the POST Sign, use the Verify GET method to move the conversation to the final confirmation stage "
sidebar: em_sidebar
permalink: em_conversation_verify.html
folder: prodEmandates
simple_map: true
map_name: usermap
box_number: 4
---

In the Verify stage of the conversation, use the GET method to render the screen to prompt the user for the SMS <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.otp}}">OTP</a> code (which the user will have received on his/her mobile phone). 

Move to the final stage in the conversation: [Confirmation](em_conversation_confirm.html)

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 

 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/verifyGetUsingGET','#profileTabs',timerRef); }, 500);



</script>


<div id="mydiv"></div>


</div>
</div>



{% include links.html %}
