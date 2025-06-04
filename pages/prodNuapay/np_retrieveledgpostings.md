---
title: Retrieve Ledger Account Postings
keywords: Retrieve Ledger Account Postings
summary: "Retrieve Ledger Account Postings RESTful API"
sidebar: acc_sidebar
permalink: np_retrieveledgpostings.html
folder: prodNuapay
toc: true
---

## API Details

Use this service to retrieve the postings (debit and credit entries) on a specific ledger account (`ledgerAccountId`).

{% include swagger_pa.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/posting-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listLedgerAccountPostingsUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
