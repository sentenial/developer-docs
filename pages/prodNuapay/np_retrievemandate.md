---
title: Retrieve Mandate
keywords: Retrieve Mandate API
summary: "Retrieve Mandate RESTful API"
sidebar: np_sidebar
permalink: np_retrievemandate.html
folder: prodNuapay
toc: false
---

## API Details

The Retrieve Mandate call allows you to view the details of a specific mandate as stored in Nuapay.

The request requires that you provide the Mandate resource identifier (as returned in the <a href="np_createmandate.html">Create Mandate</a> call)

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/viewMandateUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
