---
title: List Accounts
keywords: List Accounts API
summary: "List Accounts RESTful API"
sidebar: np_sidebar
permalink: np_listaccounts.html
folder: prodNuapay
toc: false
---

## API Details

The List Accounts request allows you to view a collection of accounts linked to you as a Nuapay merchant.

{% include note.html content="Because there are no required fields in this request, if you do not want to provide any parameters, you must supply an empty JSON body using {}" %}

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
