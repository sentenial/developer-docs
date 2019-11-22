---
title: View Transaction
keywords: View Transaction
summary: "View Transaction RESTful API"
toc: false
sidebar: np_sidebar
permalink: np_viewtransaction.html
folder: prodNuapay
toc: false
---

## API Details

Following a <a href= "np_listtransactions.html">List Transaction</a> request you can use a returned resource URI to retrieve the details of an individual transaction.
The various transaction types that are possible are described in the table in the <a href = "np_transactionoverview.html">Transaction Overview</a> section.

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
