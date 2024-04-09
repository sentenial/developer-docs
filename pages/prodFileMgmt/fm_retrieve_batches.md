---
title: Retrieve Batches
keywords: Retrieve Batches
summary: "Use this service to retrieve the batches linked to an individual file."
sidebar: fm_sidebar
permalink: fm_retrieve_batches.html
folder: prodFileMgmt
---
Within individual files:

* Transactions are batched.
* A file may have 1-n batches.

Use this endpoint to retrieve all the batches with an individual file. You must provide a unique `Id`.
To retrieve a `fileId`, see the `200` response to the [Retrieve Files](fm_retrieve_files.html) request.


{% include swagger_fm.html %}

{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-files-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listBatchesUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
