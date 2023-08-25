---
title: List Credit Transfers
keywords: List Credit Transfers API
summary: "List Credit Transfers RESTful API"
sidebar: ct_sidebar
permalink: np_listcts.html
folder: prodNuapay
toc: true
---

## API Details

The List Credit Transfers request allows you to view a collection of Credit Transfers linked to a:

* Single beneficiary
* All beneficiaries

Use an appropriate URI (as described below) to return the required collection of CTs.

{% include swagger_np.html %}

{% include urls.html %}

## List CTs Linked to a Single Beneficiary

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listCreditTransfersBeneficiaryUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

## List ALL CTs (Linked to an Originator)


<ul id="profileTabs2" class="nav nav-tabs">
</ul>

{% include redoc.html %}

var timerRef2 = setInterval(function() { getDocs('operation/listCreditTransfersUsingGET','#profileTabs2',timerRef2); }, 500);
</script>
</div>
</div>


{% include links.html %}
