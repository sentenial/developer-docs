---
title: Create Credit Transfer Batches
keywords: Create CT Batches
summary: "Create CT Batch RESTful API"
sidebar: ct_sidebar
permalink: np_ctcreatecoll.html
folder: prodNuapay
toc: false
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %}

* The `POST /credittransfers/batches` API allows you to initiate multiple credit transfer transactions with a single request.
* This API supports various schemes and currencies by incorporating key ISO20022 XML attributes.
* The request should include details about the batch, such as reference, batch booking preference, number of transactions, total amount, currency, etc.
* Additionally, the request should include payment information objects for each transaction.
* The API processes the request asynchronously and provides a response object with a unique batch ID, which can be used to track the status of the batch.
* This API is a part of a larger system that allows you to creation and manage credit transfer batches.


{% include idempotency.html %}

{% include swagger_ct.html %}

{% include urls.html %}

{% include tip.html content="The Batch CT APIs are Asynchronous and available under the <a href='https://sentenial.github.io/credit-transfers/docs/redoc-v2.html#tag/Credit-Transfers-Collections' target ='_new'> v2 CT Swagger </a>." type="primary"  %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/credit-transfers/docs/redoc-v2.html');
var timerRef = setInterval(function() { getDocs('operation/addCreditTransferBatchUsingPOST','#profileTabs',timerRef); }, 500);


</script>
<div id="mydiv"></div>


</div>
</div>


{% include links.html %}
