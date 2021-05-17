---
title: Sign Conversation 
keywords: Sign Conversation
summary: "Use the GET and POST methods to retrieve the manate details and then capture when payers sign."
sidebar: em_sidebar
permalink: em_sign.html
folder: prodEmandates
---

The Sign Conversation API use:

* GET to retrieve the mandate details initially.
* POST to push the conversation to the next setp.

To present the mandate for signing:

* Use the `GET /conversations/sign` to retireve the mandate details (i.e. the details provided in [Prepare E-Mandate](em_prepare.html))
* Render the E-Mandate signup page.
* When the end user clicks the Proceed button on the signup page, use `POST/conversations/sign` to move the e-mandate to the next conversation step.

{% include swagger_em.html %}


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
