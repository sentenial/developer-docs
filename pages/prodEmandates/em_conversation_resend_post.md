---
title: Resend Conversation Step - Resend the OTP
keywords: E-Mandate Conversation - Resend Sign
summary: "Use the Resend service to dispatch a new OTP to the  debtor."
sidebar: em_sidebar
permalink: em_conversation_resend_post.html
folder: prodEmandates
simple_map: true
map_name: usermap2
box_number: 3
---

The user, at this point in the process, has been prompted to provide the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.otp}}">OTP</a> but cannot proceed and has requested a new code to be issued. The payer may contact the merchant directly or you may want to design a **Resend Code** button to your Signup page.

* Call `POST /conversations/resend` to issue a new <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.otp}}">OTP</a>. 
* The user will receive a new email with a new code included. (Note that if SMS authentication is being used then a new SMS is dispatched)

Move to the next stage in the conversation: [Confirmation](em_conversation_resend_confirm.html)

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 

 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/resendOtpPostUsingPOST','#profileTabs',timerRef); }, 500);



</script>


<div id="mydiv"></div>


</div>
</div>


{% include links.html %}
