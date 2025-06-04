---
title: Create Collective Account
keywords: Create Collective Account
summary: "Create Collective Account RESTful API"
sidebar: acc_sidebar
permalink: np_createcollaccount.html
folder: prodNuapay
toc: true
---

## API Details

To work with Ledger Accounts, you must first create a **Collective Account** of type `LEDGER`. This account acts as a required parent for all Ledger Accounts.

Note that:

* Ledger Accounts are child accounts grouped under a Ledger Collective Account, enabling organised and scalable account management.
* When creating a Ledger Account you must include the `collectiveAccountId` of a parent `LEDGER` Collective Account in the request path.
* Attempting to use a non-`LEDGER` type (e.g., `CUSTOMER` or `OFFICE`) will result in an error.
* A `LEDGER` Collective Account provides a summary of its child accounts:
  - Aggregated balances
  - Combined intraday transactions
* The total balance of a Ledger Collective Account is calculated by summing the balances and intraday activity of all its child Ledger Accounts.

{% include tip.html content="Always ensure the parent account is of type `LEDGER` before attempting to create a Ledger Account." %}




{% include swagger_pa.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/posting-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/openCustomerCollectiveAccountUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
