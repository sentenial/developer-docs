---
title: Retrieve Direct Debit
keywords: Retrieve Direct Debit
summary: "Retrieve Direct Debit RESTful API"
toc: false
sidebar: np_sidebar
permalink: np_retrievedirectdebit.html
folder: prodNuapay
toc: false
---

## API Details

The Retrieve Direct Debit request allows you return the details of a given Direct Debit payment.

The payment's ID, URI, end-to-end, collection date etc. are all returned.

The request requires that you provide the:

* Resource Mandate ID
* Resource Direct Debit ID


{% include swagger_np.html %}

{% include urls.html %}

{% include tip.html content="You must use the resource identifier of the `schemeId`/ `mandateId`/ `directDebitId` in your requests and not the actual creditor scheme ID/SUN or Unique Mandate Reference or Direct Debit identifier. Resource identifiers are short alphanumeric strings, similar to this: abxq9kq52l. Depending on the request you may need 1, 2 or all 3 of these resource identifiers in your URI." %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/viewDirectDebitUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
