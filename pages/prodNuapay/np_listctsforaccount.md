---
title: List Credit Transfers for Account
keywords: List the Credit Transfer transactions linked to an account
summary: "List Credit Transfers for Account RESTful API"
toc: false
sidebar: acc_sidebar
permalink: np_listctsforaccount.html
folder: prodNuapay
toc: false
---

## API Details

Use this request to return the list the credit transfer transactions linked to an account.
Pass the account `Id` retrieved in the response to the [List Accounts](np_listaccounts.html) request as a path parameter.

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listCreditTransfersForAccountUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
