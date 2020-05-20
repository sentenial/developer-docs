---
title: Revoke all Direct Debits
keywords: Revoke all Direct Debits
summary: "Revoke all Direct Debits RESTful API"
sidebar: np_sidebar
permalink: np_revokealldds.html
folder: prodNuapay
toc: false
---

## API Details

As detailed in the [Revoke Direct Debit](np_revokedirectdebit.html) section, it is possible to revoke a single Direct Debit payment that is in `READY_FOR_EXPORT` status. The Revoke All Direct Debits request allows you to revoke a number of payments, linked to a specific mandate/DDI, in a single request (for a fixed-length schedule).

{% include important.html content="Note that in a fixed-length [payment schedule](np_schedulesoverview.html) (e.g. 12 payments, €10 per Direct Debit) all payments are created in READY_FOR_EXPORT status when you create the payment schedule. When you use the Revoke All Direct Debits request, all these payments are revoked. In an open-ended schedule only one payment is created in READY FOR EXPORT at any point in time; when one payment is exported a new payment is created in READY FOR EXPORT status. When you use Revoke All against an open-ended schedule, only one payment is revoked and a new payment will be create in `READY_FOR_EXPORT`." %}


{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/revokeAllDirectDebitsUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
