---
title: List Sub-Accounts
keywords: List the sub-accounts linked to a master (current) account
summary: "List Sub-Accounts RESTful API"
toc: false
sidebar: acc_sidebar
permalink: np_listsubaccount.html
folder: prodNuapay
toc: false
---

## API Details

Use this request to return the list of sub-accounts under a master account.
Pass the account `Id` retrieved in the response to the [List Accounts](np_listaccounts.html) request.

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listSubAccountsUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
