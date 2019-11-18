---
title: Create Credit Transfer & Beneficiary
keywords: Create Credit Transfer & Beneficiary
summary: "Create Credit Transfer & Beneficiary RESTful API - generate a payment and its beneficiary in a single API call."
sidebar: np_sidebar
permalink: np_createctandbene.html
folder: prodNuapay
toc: false
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %} 

The Create Credit Transfer request requires that you have first created a beneficiary. In some scenarios it is simpler to generate both the beneficiary and the payment at the same time and this request allows you to do that. 

{% include note.html content="If the beneficiary details you reference in the request have been previously provided (and that beneficiary is already stored against your merchant profile) Nuapay will reuse that stored beneficiary data: a new beneficiary is only created if his/her beneficiary account has not been referenced before in a previous Credit Transfer payment." %}

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addCTBeneficiaryOnFlyUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>



{% include links.html %}
