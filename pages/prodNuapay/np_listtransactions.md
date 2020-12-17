---
title: List Transactions
keywords: List Transactions API
summary: "List Transactions RESTful API"
sidebar: np_sidebar
permalink: np_listtransactions.html
folder: prodNuapay
toc: false
---

## API Details

Note that:
* The List Transactions request allows you to view all the transactions linked to a specific Nuapay merchant account.
* The various transaction types that are possible are described in the table in the [Transaction Overview](np_transactionoverview.html) section.

{% include tip.html content="When specifying a `valueDateFrom` and `valueDateTo` you must provide the values in miliseconds (the Unix Epoch)." %}


{% include note.html content="Because there are no required fields in this request, if you do not want to provide any parameters, you must supply an empty JSON body using {}. Filtering based on timestamps and based on the value of the transactions is also possible." %}

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listTransactionsUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
