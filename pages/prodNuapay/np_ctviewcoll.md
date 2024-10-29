---
title: View a Credit Transfer Collection
keywords: View a CT Collection
summary: "View a CT Collection RESTful API"
sidebar: ct_sidebar
permalink: np_ctviewcoll.html
folder: prodNuapay
toc: false
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %}

* The `GET /credittransfers/collections/{collectionId}` endpoint allows you to retrieve information about a specific collection using its unique ID, which is generated during the creation process using the`POST /credittransfers/collections` API.
* This endpoint returns a response object similar to the one from the POST request, including details such as the collection ID, reference, requested execution date, actual execution date, number of transactions, total amount, etc.
* Additionally, this endpoint provides access to view the credit transfers associated with a particular collection (through a link to the `GET /credittransfers/collections/{collectionId}/credittransfers)` endpoint.
* The response will display different collection statuses depending on the stage of processing, ranging from `QUEUED` to `COMPLETE` or `COMPLETE WITH ERRORS` (see [Credit Transfer Statuses](np_ctstatuses.html) for details on the various possible statuses).


{% include swagger_ct.html %}

{% include urls.html %}

{% include tip.html content="The Collections CT APIs are Asynchronous and available under the <a href='https://sentenial.github.io/credit-transfers/docs/redoc-v2.html#tag/Credit-Transfers-Collections' target ='_new'> v2 CT Swagger </a>." type="primary"  %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/credit-transfers/docs/redoc-v2.html');
var timerRef = setInterval(function() { getDocs('operation/viewCollectionUsingGET','#profileTabs',timerRef); }, 500);


</script>
<div id="mydiv"></div>


</div>
</div>


{% include links.html %}
