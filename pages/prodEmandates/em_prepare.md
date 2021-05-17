---
title: Prepare E-Mandate 
keywords: E-Mandate Token
summary: "The Prepare E-Mandate API returns a session identifier or token required to initiate the e-mandate conversation."
sidebar: em_sidebar
permalink: em_prepare.html
folder: prodEmandates
---

E-Mandates may be used in the following modes:

* [Overlay](em_overlay.html)
* [Redirect](em_redirect.html)
* [Direct API Integration](em_directapioverview.html)

Regardless of the approach you take, the Prepare E-Mandate API is required.

An E-Mandate token is a session ID that is the starting point for your electronic mandate.

{% include important.html content="An E-Mandate token has an expiry date / time-to-live (TTL) of 30 days from its creation date." %}

The Token encapsulates the following:

* Your Merchant configurations (Signing Method, UI customisations, Debtor/Payer Input Allowed, etc.)
* Merchant-specific details (Creditor Scheme ID, Scheme Type, etc.)
* Payer details (Address details, phone details, email, etc.)
* Contract Identifier (optional, if you want to combine a contract and mandate - see <a href="em_contractoverview.html">E-mandate and Contract</a>)

{% include note.html content="Because we use tokens, your customers' sensitive account details are never stored on your server." %}


{% include swagger_em.html %}


{% include urls.html %}

To retrieve your token you must make a <b>Prepare E-Mandate</b> request:


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 
 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/prepareMandateUsingPOST','#profileTabs',timerRef); }, 500);



</script>


<div id="mydiv"></div>


</div>



</div>




{% include links.html %}
