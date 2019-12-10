---
title: HTTP Response Codes
keywords: HTTP Response Codes 
summary: "All APIs respond with a HTTP code: 200 and 201 indicate success, the meaning for other codes are provided below."
sidebar: em_sidebar
permalink: em_httpreasons.html
folder: prodEmandates
toc: true
datatable: true
---

## HTTP Codes

{% include http-codes.html %}

## The JSON Object Returned in the 400 and 422 Responses

When a `400` or a `422` response is returned, the body will contain a JSON object that describes the problem. 

The `400` response error object has the following structure:

|**Path**| **Type**|**Description**|
|returnCode| String| Error Type Code (see below)|
|returnDescription|	String|	Error description (see below)|
|details| Array| The object holds a collection of validation errors. It is returned only where `returnCode` equals `8002`.|
|details[].code| String |Error Code (see below)|
|details[].field| String | JSON path to the request object property to which the error is related|
|details[].description|	Error description| The description|

The `422` response error object has this structure:

|**Path**| **Type**|**Description**|
|returnCode| String| Error Type Code (see below)|
|returnDescription|	String|	Error description (see below)|
|details| Null| Only returned where `returnCode` equals `8002` and holds a list of input validation errors.|



## Error Details

See the possible error codes in the table below:

<ul id="profileTabs" class="nav nav-tabs">
  
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('tag/Error-Codes','#profileTabs',timerRef); }, 500);
</script>
<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
