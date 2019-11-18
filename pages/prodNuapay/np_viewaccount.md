---
title: View Account
keywords: View Account
summary: "View Account RESTful API"
toc: false
sidebar: np_sidebar
permalink: np_viewaccount.html
folder: prodNuapay
toc: false
---

## API Details

Use this request to view the details of an account by referencing the resource ID returned in the <a href="np_createaccount.html">Create Account</a> or <a href="np_listaccounts.html">List Accounts</a> calls.

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/viewAccountUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
