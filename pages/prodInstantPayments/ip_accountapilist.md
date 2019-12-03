---
title: List Account
keywords: List Account API
summary: "Use this service to retrieve the URI of your Origix IP Technical Account (or Shadow Account). This is required for subsequent calls to other Account services."
sidebar: ip_sidebar
permalink: ip_accountapilist.html
folder: prodNuapay
toc: false
---

## API Details

Use the List Account service to retrieve the URI for your Origix IP Technical account.

This URI will be used later in the List Transactions and View Transaction API requests.



{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listAccountsUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
