---
title: Retrieve Transaction
keywords: View Transaction
summary: "View Transaction RESTful API"
toc: false
sidebar: acc_sidebar
permalink: np_viewtransaction.html
folder: prodNuapay
toc: false
---

## API Details

Following a <a href= "np_listtransactions.html">List Transaction</a> request you can use a returned resource URI to retrieve the details of an individual transaction.

{% include tip.html content="The various transaction types that are possible are described in the table in the [Transaction Overview](np_transactionoverview.html) section." %}


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
