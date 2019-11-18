---
title: List Beneficiaries
keywords: List Beneficiaries API
summary: "List Beneficiaries RESTful API"
sidebar: np_sidebar
permalink: np_listbeneficiaries.html
folder: prodNuapay
toc: false
---

## API Details

The List Beneficiary request returns the details of all beneficiaries that are set up under your Nuapay Merchant account.

The beneficiaries' unique resource IDs, URIs, address details (if stored) and bank details are all returned.

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listBeneficiariesUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>




{% include links.html %}
