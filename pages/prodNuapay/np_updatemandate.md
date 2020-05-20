---
title: Update Mandate / DDI
keywords: Update Mandates API
summary: "Update Mandates RESTful API"
sidebar: np_sidebar
permalink: np_updatemandate.html
folder: prodNuapay
toc: false
---

## API Details

You may need to make updates to mandates/DDIs at various points. Where a payer informs you that address details or an account has changed, for example, it is important to update this data so that Direct Debit payments will continue to be processed as normal.

You may need to re-send the mandate/DDI for signature depending on the update that is being made to the mandate/DDI. 

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
