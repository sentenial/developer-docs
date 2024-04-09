---
title: Retrieve a Single File
keywords: Retrieve Single File
summary: "Use this service to return details of a single file."
sidebar: fm_sidebar
permalink: fm_retrieve_single_file.html
folder: prodFileMgmt
---
Use this endpoint to retrieve details of an individual file. You must provide a unique `Id`.

To retrieve a `fileId`, see the `200` response to the [Retrieve Files](fm_retrieve_files.html) request.



{% include swagger_fm.html %}

{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-files-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/retrieveFileDetailsUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
