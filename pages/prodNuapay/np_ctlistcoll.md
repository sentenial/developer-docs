---
title: List Credit Transfer Collections
keywords: List CT Collection
summary: "List CT Collection RESTful API"
sidebar: ct_sidebar
permalink: np_ctlistcoll.html
folder: prodNuapay
toc: false
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %}

* The `/credittransfers/collections` endpoint allows you to retrieve a list of all collections that have been created.
* This endpoint supports filtering by various parameters, such as reference,creation date range, and originator IBAN, making it easier to locate specific collections.
* The response follows the collection envelope structure defined in the swagger documentation and provides information similar to that returned by the `POST /credittransfers/collections` API, including details like collection ID, reference, batch booking preference, type, status, creation date, etc.
* Additionally, the `pagesize` parameter allows you to set the number of collections returned on a single page.


{% include swagger_ct.html %}

{% include urls.html %}

{% include tip.html content="The Collections CT APIs are Asynchronous and available under the <a href='https://sentenial.github.io/credit-transfers/docs/redoc-v2.html#tag/Credit-Transfers-Collections' target ='_new'> v2 CT Swagger </a>." type="primary"  %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/credit-transfers/docs/redoc-v2.html');
var timerRef = setInterval(function() { getDocs('operation/listCollectionsUsingGET','#profileTabs',timerRef); }, 500);


</script>
<div id="mydiv"></div>


</div>
</div>



{% include links.html %}
