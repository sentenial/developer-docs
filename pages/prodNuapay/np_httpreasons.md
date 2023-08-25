---
title: HTTP Response Codes
keywords: HTTP Response Codes
summary: "All APIs respond with a HTTP code. 200 and 201 indicate success, the meaning for other codes are provided below."
sidebar: resources_sidebar
permalink: np_httpreasons.html
folder: prodNuapay
toc: true
datatable: true
---

## HTTP Codes

{% include http-codes.html %}

## The JSON Object Returned in the 400 and 422 Responses

When a `400` or a `422` response is returned, the body will contain a JSON object that describes the problem.

The error object has the following structure:

|**Path**| **Type**|**Description**|
|returnCode| String| Error Code (see below)|
|returnDescription|	String|	Error description (see below)|
|details| Array| The object holds a collection of validation errors. It is returned only where `returnCode` equals to `8888` or `9999`.|
|details[].code| String |Error Code (see below)|
|details[].field| String | JSON path to the request object property to which the error is related|
|details[].description|	Error description| The description|
|details[].resourceUri| String | This property holds existing resource URI in case the validation error states the resource already exist and can't be created. It is returned only for `returnCode` equal to `9999`.|

## Error Details

See the possible error codes in the table below:

<ul id="profileTabs" class="nav nav-tabs">

</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('tag/Error-Codes','#profileTabs',timerRef); }, 500);
</script>
<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
