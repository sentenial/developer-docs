---
title: Update Mandate
keywords: Update Mandates API
summary: "Update Mandates RESTful API"
sidebar: np_sidebar
permalink: np_updatemandate.html
folder: prodNuapay
toc: false
---

## API Details

You may need to make updates to mandates at various points. Where a payer informs you that address details or an account has changed, for example, it is important to update this data so that Direct Debit payments will continue to be processed as normal.

You may need to re-send the mandate for signature depending on the update that is being made to the mandate. 
We would recommend that a mandate is approved by your payer if any of the following <b>key mandate fields</b> are modified:

* The Unique Mandate Reference (the SEPA Mandate ID)
* Payer account data

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/editMandateUsingPUT','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>





{% include links.html %}
