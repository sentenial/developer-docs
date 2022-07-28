---
title: Cancel Payment Schedule
keywords: sample
summary: "Cancel Payment Schedule RESTful API"
sidebar: np_sidebar
permalink: np_cancelschedule.html
folder: prodNuapay
toc: false
---

## API Details

In a <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.schedule-fixed}}">Fixed-Length</a> schedule the **Cancel Payment Schedule** request will set the status of any `READY_FOR_EXPORT` Direct Debit transactions in that schedule to `REVOKED`.

In an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.schedule-open}}">Open-Ended</a> schedule the current `READY_FOR_EXPORT` payment is updated to `CANCELLED` and no additional payments will be added.

{% include important.html content="Direct Debits that have been EXPORTED are unaffected by the cancel payment schedule request" %}

(See [Direct Debit Statuses](np_ddstatuses.html) for more information on the various payment statuses that are possible).


{% include idempotency.html %}

{% include swagger_np.html %}

{% include urls.html %}

{% include tip.html content="You must use the resource identifier of the `schemeId`/ `mandateId`/ `paymentScheduleId` in your requests and not the actual creditor scheme ID/SUN or Unique Mandate Reference or payment schedule identifier. Resource identifiers are short alphanumeric strings, similar to this: abxq9kq52l. Depending on the request you may need 1, 2 or all 3 of these resource identifiers in your URI." %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/cancelPaymentScheduleUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
