---
title: List Credit Transfers in a Batch
keywords: List CTs in a Batch
summary: "List CTs in a Batch RESTful API"
sidebar: ct_sidebar
permalink: np_ctlistctcoll.html
folder: prodNuapay
toc: false
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %}

* The `GET /credittransfers/batches/{creditTransferBatchId}/credittransfers` endpoint allows you to view all the payments connected to a batch of CT payments.
* This endpoint reuses the same object structure as the standard credit transfer endpoint, ensuring consistency across the API.
* You can filter the list of credit transfers using parameters such as end-to-end ID, beneficiary IBAN, beneficiary name, and execution date range.
* For batches with a status of `QUEUED`, the endpoint returns an `HTTP 202 (ACCEPTED)` response with no body, indicating that the list of credit transfers is not yet available.
* For other batch statuses, the endpoint returns a standard HTTP 200 (OK) response containing a list of credit transfer objects with details like originator IBAN, requested and actual execution dates, payment amount and currency, end-to-end ID, remittance information, payment status, type, and payment scheme.

{% include swagger_ct.html %}

{% include urls.html %}

{% include tip.html content="The Batch CT APIs are Asynchronous and available under the <a href='https://sentenial.github.io/credit-transfers/docs/redoc-v2.html#tag/Credit-Transfers-Collections' target ='_new'> v2 CT Swagger </a>." type="primary"  %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/credit-transfers/docs/redoc-v2.html');
var timerRef = setInterval(function() { getDocs('operation/listCreditTransfersBatchUsingGET','#profileTabs',timerRef); }, 500);


</script>
<div id="mydiv"></div>


</div>
</div>
