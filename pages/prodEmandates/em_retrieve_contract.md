---
title: Download Contract
keywords: Retrieve Contract
summary: "Use this service to download a PDF representation of the contract."
sidebar: em_sidebar
permalink: em_retrieve_contract.html
folder: prodEmandates
---

Use this service to retrieve the PDF version of the contract.
A `200 OK` response returns the PDF binary. 

|You must have first retrieved the E-Mandate token via the [Prepare Mandate](em_prepare.html) before you can call this APIs|


{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 

 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/conversationContractGetUsingGET','#profileTabs',timerRef); }, 500);



</script>


<div id="mydiv"></div>


</div>
</div>
{% include links.html %}
