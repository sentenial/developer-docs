---
title: Create Payment Schedule & Mandate/DDI
keywords: Create Payment Schedule & Mandate
summary: "Create Payment Schedule & Mandate RESTful API"
sidebar: np_sidebar
permalink: np_createschedulemandate.html
folder: prodNuapay
toc: false
---

## API Details

As outlined in <a href = "np_createschedule.html">Create Payment Schedule</a>, before you can add a schedule of Direct Debit payments for a payer you must first have an `ACTIVE` mandate/DDI in place; so two separate requests are required: one to create and activate a mandate and a second to add the schedule of payments.

The **Create Payment Schedule and Mandate** service allows you to combine these two request so that you can create a mandate/DDI and a payment schedule in a single request.

{% include note.html content="A successful request will result in a new mandate/DDI and a schedule of direct debits being created. If the request is unsuccessful neither a mandate/DDI nor any direct debits will be created." %}

{% include idempotency.html %}

{% include swagger_np.html %}

{% include urls.html %}


{% include tip.html content="You must use the resource identifier of the `schemeId`/ `mandateId`/ `paymentScheduleId` in your requests and not the actual creditor scheme ID/SUN or Unique Mandate Reference or payment schedule identifier. Resource identifiers are short alphanumeric strings, similar to this: abxq9kq52l. Depending on the request you may need 1, 2 or all 3 of these resource identifiers in your URI." %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addPaymentScheduleUsingPOST_1','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
