---
title: Revoke Direct Debit
keywords: Revoke Direct Debit
summary: "Revoke Direct Debit RESTful API"
sidebar: np_sidebar
permalink: np_revokedirectdebit.html
folder: prodNuapay
toc: false
---

## API Details

When you first create a Direct Debit it has a status of `READY_FOR_EXPORT`. Once it is forwarded from Nuapay on to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing</a> or to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.bacs-clearing}}">Bacs</a> for processing, its status is updated to `EXPORTED`.

If you decide that you do not want to settle the payment and do not want to pass it on for further processing at Clearing, you may revoke it.


{% include tip.html content="The Revoke operation is only possible for payments that are in READY_FOR_EXPORT status. For more information see [Direct Debit Statuses](np_ddstatuses.html)." %}


{% include idempotency.html %}

{% include swagger_np.html %}

{% include urls.html %}

{% include tip.html content="You must use the resource identifier of the `schemeId`/ `mandateId`/ `directDebitId` in your requests and not the actual creditor scheme ID/SUN or Unique Mandate Reference or Direct Debit identifier. Resource identifiers are short alphanumeric strings, similar to this: abxq9kq52l. Depending on the request you may need 1, 2 or all 3 of these resource identifiers in your URI." %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/revokeDirectDebitUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
