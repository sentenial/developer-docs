---
title: Resend One-Time-Password
keywords: Resend OTP
summary: "Use where Email or SMS authorisation is being used and the payer requires an OTP to be reissued."
sidebar: em_sidebar
permalink: em_resend.html
folder: prodEmandates
---

For a worked example of a resend One-Time-Password (OTP) process, see the [Resend Conversation](em_conversation_resend_settings.html) example.

When you use this service it is assumed:

* You have created an e-mandate and have issued an OTP to the payer.
* The payer has lost that code (for example, the user deletes the SMS or email message in error)
* The payer has requested that a new code is issued.

Note that an OTP can be retried up to a maximum of 5 times. On the 5th retry the `resend` view is not available.

|You must have first retrieved the E-Mandate token via the [Prepare Mandate](em_prepare.html) before you can call this APIs|


{% include urls.html %}

## GET /conversation/resend OTP

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 

 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/resendOtpPostUsingGET','#profileTabs',timerRef); }, 500);



</script>


<div id="mydiv"></div>


</div>
</div>

## POST /conversation/resend OTP

<ul id="profileTabs2" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef2 = setInterval(function() { getDocs('operation/resendOtpPostUsingPOST','#profileTabs2',timerRef2); }, 500);
</script>
</div>
</div>


{% include links.html %}
