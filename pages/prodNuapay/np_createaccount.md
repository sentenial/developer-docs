---
title: Create Account
keywords: Create Account
summary: "Create Account RESTful API"
sidebar: np_sidebar
permalink: np_createaccount.html
folder: prodNuapay
toc: false
---

## API Details

The Create Account request allows you to generate a new Nuapay account. You may create a current account or (optionally and depending on your merchant configuration) a sub-account.

{% include important.html content="It is possible to generate a Master or a Sub-Account. Note that sub-accounts may only be used for processing Credit Transfer payments. Note too that your merchant must be configured by Nuapay Client Services team to allow you to create a sub-account. For more information please contact your Account Manager." %}

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addAccountUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
