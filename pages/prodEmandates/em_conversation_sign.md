---
title: SMS Authentication Conversation Step - Sign
keywords: E-Mandate Conversation - Sign
summary: "Use the Sign service to allow your debtor to authorise the electornic mandate via SMS, One-Time Password."
sidebar: em_sidebar
permalink: em_conversation_sign.html
folder: prodEmandates
simple_map: true
map_name: usermap
box_number: 3
---

At this point in the conversation we are ready for the user to sign the electronic mandate.

* As an initial step, call `GET /conversations/sign` to retrieve the mandate details (the details as provided in the [Prepare E-Mandate](em_tokendirectapi.html) request).
* Render the E-Mandate signup page. 
* When the end user clicks the **Proceed** button on the signup page, use `POST/conversations/sign` to move the e-mandate to the next conversation step. Note that `email` and `mobileNumber` are mandatory in the request.

As the authorisation method in this example is `SMS_PASSWORD`, The user will receive an SMS message with a 4-digit code to the mobile number specified. The user will need to submit this code when prompted (in the next conversation step). Note that this <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.otp}}">OTP</a> is not returned in the API.

Move to the next stage in the conversation: [Confirmation](em_conversation_confirm.html)

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
