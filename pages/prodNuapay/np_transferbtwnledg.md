---
title: Transfer Between Ledger Accounts
keywords: Retrieve Ledger Account Postings
summary: "Retrieve Ledger Account Postings RESTful API"
sidebar: acc_sidebar
permalink: np_transferbtwnledg.html
folder: prodNuapay
toc: true
---

## API Details

Use this service to make transfers between two Ledger accounts. Note that the `accountFrom` and the `accountTo` values must both be Ledger Accounts.

{% include swagger_pa.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/posting-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/postLedgerAccountTransfersUsingPost','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
