---
title: Create Ledger Account
keywords: Create Ledger Account
summary: "Create Ledger Account RESTful API"
sidebar: acc_sidebar
permalink: np_createledgaccount.html
folder: prodNuapay
toc: true
---

## API Details

Use this service to create a Ledger Account under a specific Collective Account (`collectiveAccountId`).

{% include swagger_pa.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/posting-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/openLedgerAccountUsingPost','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
