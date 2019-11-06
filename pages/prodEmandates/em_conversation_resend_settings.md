---
title: Resend Conversation Step - Settings
keywords: E-Mandate Conversation - Settings
summary: "The GET Conversation settings allows you to verify your E-Mandate configuration and to see the next available steps in your current conversation"
sidebar: em_sidebar
permalink: em_conversation_resend_settings.html
folder: prodEmandates
simple_map: true
map_name: usermap2
box_number: 1
---

|Before calling any of the conversation APIs, you must first make a request to [Prepare Emandate](em_tokendirectapi.html) and retrieve an E-Mandate token. This token must be provided in your HTTP `Token` header.|

In this conversation example, we are assuming that: 
* You are creating an e-mandate and will issue an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.otp}}">OTP</a> to the payer. 
* The payer will lose that code (for example, the user deletes the SMS or email message in error) 
* The payer has requested that a new code is issued. 

In this example, we will assume that the authentication method is set to EMAIL. Note that the conversation steps outlined here are also applicable where the authorization type is configured as `SMS_PASSWORD`

To begin: 

* Confirm that you have been properly configured for this authentication method.
* Generate a GET request to `/conversations/settings` 
* Confirm in the response that  ``authorization`` is  `EMAIL_PASSWORD`.


{% include note.html content="It is not possible to set up your authentication configuration via the API; a member of the Nuapay Customer Support team will set up your business as requested. See [Configurations](em_configuration.html#configurations) for details on what configurations are possible." %}

Move to the next stage in the conversation: [Signing](em_conversation_resend_sign.html)

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
