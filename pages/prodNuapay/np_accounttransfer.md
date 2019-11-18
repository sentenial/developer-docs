---
title: Transfer Between Accounts
keywords: Transfers API
summary: "Transfers RESTful API"
sidebar: np_sidebar
permalink: np_accounttransfer.html
folder: prodNuapay
toc: false
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %} 

Where you have been configured with more than a single Nuapay account, `POST \transfer` allows you to move funds between your accounts.

It is possible to transfer between:

1. Two current accounts.
1. Two sub-accounts (provided both are under the same current account).

**It is not possible** to transfer from a current to a sub-account or from a sub-account to a current account.

{% include note.html content="It is only possible to transfer funds between accounts that have the same currency." %}

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/transferUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
