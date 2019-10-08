---
title: Versioning and Backward Compatibility
keywords: Versioning Backward Compatibility
summary: "Details on API versioning and backward compatibility"
sidebar: productOverview_sidebar
permalink: prod_versioning.html
folder: prodOverview
toc: false
---

## Versioning

Changess may be made to any of our APIs without a change in version number, provided the change follows our backwards compatibility guidelines (see below). Different versions will be managed via a HTTP header indicating the version of the API that the client is using.

Requests with no version number or an unmatched version number will be treated as version 1.0 requests.


## Backwards Compatibility

The following changes are considered to be backwards-compatible:

* Adding new API endpoints; new endpoints are independent.
* Adding new optional request parameters to existing API calls.
* Adding new response properties to existing API calls. You should pay particular attention to this point if you are mapping your JSON responses to another programming language construct.
* Changing of the property order in existing API responses.
* Changing the length of object IDs (object IDs will never exceed 255 characters).
* Changing the messages returned by validation or other error messages.
* Output Encoding Rules are applied to some services and will be applied to all services in the future.

{% include links.html %}
