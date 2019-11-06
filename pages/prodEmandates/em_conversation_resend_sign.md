---
title: Resend Conversation Step - Sign
keywords: E-Mandate Conversation - Resend Sign
summary: "Use the Sign service to allow your debtor to authorise the electornic mandate with an OTP issued via email."
sidebar: em_sidebar
permalink: em_conversation_resend_sign.html
folder: prodEmandates
simple_map: true
map_name: usermap2
box_number: 2
---

At this point in the conversation we are ready for the user to sign the electronic mandate.

* As an initial step, call `GET /conversations/sign` to retrieve the mandate details (the details as provided in the [Prepare E-Mandate](em_tokendirectapi.html) request).
* Render the E-Mandate signup page.
* When the end user clicks the **Proceed** button on the signup page, use `POST/conversations/sign` to move the e-mandate to the next conversation step. Note that `email` is mandatory in the request.

As the authorisation method in this example is `EMAIL_PASSWORD`, The user will receive an email message with a 4-digit code. 
We will assume here that after receiving the email, the user accidentially deletes the message and does not have a code to complete the signing process. 
We will need to resend the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.otp}}">OTP</a> so that the payer can complete the signup process.

Move to the next stage in the conversation: [Resending the OTP](em_conversation_resend_post.html)

{% include urls.html %}


## GET /conversation/sign

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 

 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/signMandateGetUsingGET','#profileTabs',timerRef); }, 500);



</script>


<div id="mydiv"></div>


</div>
</div>

## POST /conversation/sign

<ul id="profileTabs2" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef2 = setInterval(function() { getDocs('operation/signMandatePostUsingPOST','#profileTabs2',timerRef2); }, 500);
</script>
</div>
</div>



{% include links.html %}
