---
title: Retrieve Document
keywords: Retrieve Document
summary: "Use this service to retrieve the PDF representation of the mandate."
sidebar: em_sidebar
permalink: em_retrieve_doc.html
folder: prodEmandates
---

Use this service to retrieve the PDF version of the mandate.
A `200 OK` response returns the PDF binary. 

|You must have first retrieved the E-Mandate token via the [Prepare Mandate](em_prepare.html) before you can call this APIs|


{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 

 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/generatePdfGetUsingGET','#profileTabs',timerRef); }, 500);



</script>


<div id="mydiv"></div>


</div>
</div>
{% include links.html %}
