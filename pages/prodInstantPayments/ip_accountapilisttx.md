---
title: List Transactions
keywords: List Account API
summary: "Use this service to retrieve transactions for a date range."
sidebar: ip_sidebar
permalink: ip_accountapilisttx.html
folder: prodInstantPayments
toc: false
---

## API Details

{% include note.html content="Before using this API request you must first retrieve the URI (the account identifier - {accountId}) for your Origix IP technical account. See [List Account](ip_accountapilist.html)." %}

 The List Transactions service retrieves transactions for a required date range.


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
