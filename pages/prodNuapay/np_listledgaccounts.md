---
title: List Ledger Accounts
keywords: List Ledger Accounts
summary: "Create Ledger Account RESTful API"
sidebar: acc_sidebar
permalink: np_listledgaccounts.html
folder: prodNuapay
toc: true
---

## API Details

Use this service to list all the ledger accounts under a specific Collective Account (`collectiveAccountId`).

{% include swagger_pa.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/posting-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listLedgerAccountsUnderCollectiveAccountUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
