---
title: Create Mandate/DDI
keywords: Mandate DDI Create Initiate Begin
summary: "Create Mandate RESTful API"
sidebar: np_sidebar
permalink: np_createmandate.html
folder: product2
toc: false
---


{% include tip.html content="If you are using E-Mandates you do not need to use this Create Mandate request." %}


## API Details

When creating mandates/DDIs, please note that:

* Mandates/DDIs must be created under a specific scheme (e.g. the SEPA CORE or Bacs scheme) and must also be linked to a Creditor Scheme ID (CSID) in SEPA or a Service User Number (SUN) for Bacs. 
* To determine your CSID/SUN use the [List Scheme](np_listcredscheme.html) service.  
* Depending on the configuration of your Creditor Scheme your mandates/DDI will be created in a specific [status](np_mandatestatuses.html). 
* Regardless of the scheme, Direct Debit payments can only be created against an **ACTIVE** mandate/DDI.

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addMandateUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
