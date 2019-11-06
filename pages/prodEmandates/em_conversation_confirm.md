---
title: SMS Authentication Conversation Step - Confirm
keywords: E-Mandate Conversation - Confirm
summary: "Use the Confirm service to prompt the user for the OTP and to retrieve the encoded identifier of the mandate created."
sidebar: em_sidebar
permalink: em_conversation_confirm.html
folder: prodEmandates
simple_map: true
map_name: usermap
box_number: 4
---

At the confirmation stage of the conversation:

* Use the `GET conversations/confirm` to render the Confirmation screen for your user.
* The user will be prompted to provide the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.otp}}">OTP</a> (this was issued in the previous step of the conversation).
* Once the user has typed the code and clicked **Submit**, call `POST conversations/confirm` to verify the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.otp}}">OTP</a>
* Once the code provided is verified, the mandate is created with the `encodedMandateId`, `encodedSchemeId` and `mandateId` being returned. Note that the mandate is now set to  `signed": true`
* An email will be triggered to the user to confirm the mandate has been activated (for SEPA) or that it has been created and will be passed to the debtor's bank (for Bacs mandates).

{% include urls.html %}


## GET / conversation/confirm

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 

 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/confirmMandateGetUsingGET','#profileTabs',timerRef); }, 500);



</script>


<div id="mydiv"></div>


</div>
</div>

## POST / conversation/confirm

<ul id="profileTabs2" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef2 = setInterval(function() { getDocs('operation/confirmMandatePostUsingPOST','#profileTabs2',timerRef2); }, 500);
</script>
</div>
</div>



{% include links.html %}
