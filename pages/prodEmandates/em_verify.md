---
title: Verify Conversation 
keywords: Verify Conversation
summary: "Use the Verify service to allow a payer to enter the E-Mandate signing flow from a link. The user verifies bu providing the last 4 digits of his/her IBAN"
sidebar: em_sidebar
permalink: em_verify.html
folder: prodEmandates
---

Where a payer is accessing an E-Mandate link e.g. from an email, the user will be prompted to provide the last 4 digits of the IBAN.

The Verify API includes:

* GET to retrieve mandate details.
* POST to push the conversation to the next step (once the payer provide the last 4 digits of his/her IBAN).

|You must have first retrieved the E-Mandate token via the [Prepare Mandate](em_prepare.html) before you can call these APIs.|


{% include urls.html %}

## GET /conversation/verify

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 

 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/verifyGetUsingGET','#profileTabs',timerRef); }, 500);



</script>


<div id="mydiv"></div>


</div>
</div>

## POST /conversation/verify

<ul id="profileTabs2" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef2 = setInterval(function() { getDocs('operation/verifyPostUsingPOST','#profileTabs2',timerRef2); }, 500);
</script>
</div>
</div>


{% include links.html %}
