---
title: View Transaction
keywords: View Transactions API
summary: "Use this service to view the details of a single transaction."
sidebar: ip_sidebar
permalink: ip_accountapiviewtx.html
folder: prodNuapay
toc: false
---

## API Details

{% include note.html content="Before using this API request you must first retrieve the URI (the account identifier - {accountId}) for your Origix IP technical account; see [List Account](ip_accountapilist.html). You will also need a specific transaction ID, returned in the [List Transactions](ip_accountapilisttx.html) request." %} 

 The View Transaction service retrieves an individual transaction.


{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/viewTransactionUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
