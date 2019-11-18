---
title: Create Payment Schedule & Mandate
keywords: Create Payment Schedule & Mandate
summary: "Create Payment Schedule & Mandate RESTful API"
sidebar: np_sidebar
permalink: np_createschedulemandate.html
folder: prodNuapay
toc: false
---

## API Details

As outlined in <a href = "np_createschedule.html">Create Payment Schedule</a>, before you can add a schedule of Direct Debit payments for a payer you must first have an Active mandate in place; so two separate requests are required: one to create and activate a mandate and a second to add the schedule of payments.

The <b>Create Payment Schedule and Mandate</b> request allows you to combine these two request so that you can create a mandate and a payment schedule in a single request.

{% include note.html content="A successful request will result in a new mandate and a schedule of direct debits being created. If the request is unsuccessful neither a mandate nor any direct debits will be created." %}

{% include swagger_np.html %}

{% include urls.html %}


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
