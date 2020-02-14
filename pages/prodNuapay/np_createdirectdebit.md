---
title: Create Direct Debit
keywords: Create Direct Debit
summary: "Create Direct Debit RESTful API"
sidebar: np_sidebar
permalink: np_createdirectdebit.html
folder: prodNuapay
toc: false
---

## API Details

The Create Direct Debit request must:

* Include the resource identifier Creditor Scheme ID (CSID) or Service User Number (SUN) (see the <a href="np_listcredscheme.html"> List Creditor Scheme</a> request)
* Reference an active mandate (its resource ID)

A successful request will result in a Direct Debit being set up in <b>READY_FOR_EXPORT</b> status: the payment is created but has not yet been forwarded to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">Clearing</a> for processing (see <a href ="np_ddstatuses.html">Direct Debit Statuses</a> for more information).

{% include tip.html content="Nuapay allows you to create a mandate and a Direct Debit payment in a single API request. For more details on this see the [Create Direct Debit and Mandate](np_createddandmand.html) request." %}


{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addSinglePaymentUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
