---
title: Confirm Conversation 
keywords: Confirm Conversation
summary: "Use the Confirm service to complete the e-mandate signup."
sidebar: em_sidebar
permalink: em_confirm.html
folder: prodEmandates
---

At the confirmation stage of the conversation:

* Use the `GET conversations/confirm` to render the Confirmation screen for your user.
* Call POST conversations/confirm (optionally pass a One-Time-Password (`code`) if you are using `EMAIl` or `SMS` authorisation.)
* The mandate is created with the `encodedMandateId`, `encodedSchemeId` and `mandateId` being returned. Note that the mandate is now set to `"signed": true`
* An email will be triggered to the user to confirm the mandate has been activated (for SEPA) or that it has been created and will be passed to the debtor’s bank (for Bacs mandates).


|You must have first retrieved the E-Mandate token via the [Prepare Mandate](em_prepare.html) before you can call this APIs|


{% include urls.html %}

## GET /conversation/confirm

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 

 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/confirmMandateGetUsingGET','#profileTabs',timerRef); }, 500);



</script>


<div id="mydiv"></div>


</div>
</div>

## POST /conversation/confirm

<ul id="profileTabs2" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef2 = setInterval(function() { getDocs('operation/confirmMandatePostUsingPOST','#profileTabs2',timerRef2); }, 500);
</script>
</div>
</div>


{% include links.html %}
