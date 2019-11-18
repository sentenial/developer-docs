---
title: Retrieve Credit Transfer
keywords: Retrieve Credit Transfer
summary: "Retrieve Credit Transfer RESTful API"
toc: false
sidebar: np_sidebar
permalink: np_retrievect.html
folder: prodNuapay
toc: false
---

## API Details

The Retrieve Credit Transfer request allows you return the details of a given Credit Transfer payment.

The payment's ID, URI, end-to-end, requested execution date etc. are all returned.

The request requires that you provide the:

* Beneficiary Resource ID
* Credit Transfer Resource ID

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/viewCreditTransferUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
