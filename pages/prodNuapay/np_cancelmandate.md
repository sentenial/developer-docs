---
title: Cancel Mandate / DDI
keywords: sample
summary: "Cancel Mandate RESTful API"
sidebar: np_sidebar
permalink: np_cancelmandate.html
folder: prodNuapay
toc: false
---

## API Details

Your payers may contact you and request that you cancel their mandate/DDI. 
* When this happens, you can use the Cancel Mandate service. This is a merchant-initiated mandate/DDI cancelation. 
* In the Bacs scheme, payers also have the option to contact their bank and request a cancelation. This is a payer-initiated cancelation; in this case the DDI cancelation is automated (see the following section). 
* It is only possible to cancel a mandate/DDI that is in `ACTIVE` status. 

When you cancel a mandate/DDI:

* Any `READY FOR EXPORT` Direct Debit transactions linked to it are automatically cancelled.
* No further collections may be made against the mandate/DDI.

If you want to engage with your payer at a later point, and want to collect direct debit payments once again, you will need to create a new mandate/DDI.

## Bacs DDI Cancelation
In the Bacs scheme: 

* Payers may request their bank to cancel the DDI that was set up with your business. 
* Where this happens, the Bacs scheme will notify Nuapay via an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.addacs}}">ADDACS</a> notification.
* Once Nuapay processes the ADDACS file, the DDI is updated to `CANCELLED` status; you will be unable to make collection against that DDI in future.

{% include tip.html content="You may want to configure the [Mandate Cancel Event](np_whmandcancel.html) Webhook so that you are notified where a payer-initiated DDI cancelation occurs." %}


{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/cancelMandateUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
