---
title: Open Banking Health Check
keywords: Health Check Availability
summary: "The Health Check service allows you to check the availability/health of ASPSP connections at a point in time"
sidebar: ob_sidebar
permalink: ob_healthoverview.html
folder: prodOpenBanking
---

## Overview

As ASPSPs may not always be available (there may be connectivity issues or scheduled downtime, for example) merchants/partners can use the Health Services to determine the availability of all ASPSPs or the health of a specific bank at any given time. 

To calculate the overall health:

* A mix of user requests and automated requests are analysed.
* Automated requests are generated every 30 seconds.
* Only requests made in the last 15 minutes are considered.
* Based on the success/failure rate against each ASPSP, a score is returned.

Where an ASPSP is deemed to be unavailable for any reason, you may decide to mark that ASPSP as unavailable on the User Interface or potentially direct the PSU to an alternative payment method.

Two services are available to allow you to retrievea a Health Score:

|**Method**|**Service**|
|<span class="label label-success">GET</span>| /status/banks | 
|<span class="label label-success">GET</span>| /status/banks/{bankId} |

## Scoring

The response to the `GET` requests referenced above, will return a `paymentServiceScore` score:

|**Score**|**Notes**|
|**0**|There are some connectivity issues. We would recommend that the merchant/partner flag this ASPSP as being currently unavailable.|
|**100**| With this score the ASPSP is available and should be selectable for the PSU.|
|**-1**| No connectivity with the ASPSP for this service|

{% include note.html content="In future releases the health check will return a score for AIS and PIS services with the ASPSP. Currently only PIS service availability is returned. AIS services will always return a score of -1 (to indicate that we do not have connectivity with the given ASPSP for the AIS service)." %}
