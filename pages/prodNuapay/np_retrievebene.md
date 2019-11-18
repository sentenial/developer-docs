---
title: Retrieve Beneficiary
keywords: Retrieve Beneficiary API
summary: "Retrieve Beneficiary RESTful API"
sidebar: np_sidebar
permalink: np_retrievebene.html
folder: prodNuapay
toc: false
---

## API Details

The Retrieve Beneficiary returns the details of a specific beneficiary.

The beneficiary's resource identifier, URI, address details (if stored) and bank details are returned.

The request requires that you provide the beneficiary resource ID:

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/viewBeneficiaryUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>



{% include links.html %}
