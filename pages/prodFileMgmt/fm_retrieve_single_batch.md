---
title: Retrieve a Single Batch
keywords: Retrieve Single Batch
summary: "Use this service to retrieve a specific batch linked to an individual file."
sidebar: fm_sidebar
permalink: fm_retrieve_single_batch.html
folder: prodFileMgmt
---
To retrieve the details of a specific batch:

* Call the [Retrieve Batches](fm_retrieve_batches.html) service.
* Get the `Id` (Batch ID) returned in the 200 response.
* Pass this unique batch identifier in this endpoint.

The response will provide you with details of the specific batch, for example:

* The `status`
* Number of transactions in the batch
* Value of transactions in the batch.


{% include swagger_fm.html %}

{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-files-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/retrieveBatchDetailsUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
