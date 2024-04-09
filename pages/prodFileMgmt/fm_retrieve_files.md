---
title: Retrieve Files
keywords: Retrieve File
summary: "Use this service to return details of files previously uploaded."
sidebar: fm_sidebar
permalink: fm_retrieve_files.html
folder: prodFileMgmt
---
## File Processing Overview

Files may be generated for Credit Transfer or Direct Debit payments and can be either:

* `IMPORT`

   OR

* `EXPORT`

Note that an `IMPORT` file:
* Is the initial file that you upload.
* It may be a .CSV file for example.
* Once processed, your file is mapped to an appropriate export format before being passed to Clearing for further processing.

The `EXPORT` file:
* Is the file that is generated in Nuapay for transmission to Clearing.
* For Bacs processing, the file type is STD-18.
* For SEPA, PAIN.001 (Credit Transfer) and PAIN.008 (Direct Debit) XML files are exported.
* The export file will include all the required details to ensure that your transactions are successfully processed.

## File Filtering

Use the `GET /files` service to retrieve ALL your files based on specific filtering conditions.

You can filter on:

* File Status
* Creation Date
* File Name
* File Type (`DIRECT_DEBIT` or `CREDIT_TRANSFER`)
* Generation type (`IMPORT` or `EXPORT`)

The following table describes the various file `statuses`:

|Status|Description|
|`QUEUED`| The file has been uploaded but has not yet been picked up by the processing engine for processing. A file will typically stay in this status for a maximum of 5 miutes.|
|`APPROVAL_PENDING`| Where Dual Authorisation has been enabled for your organisation, a file will require approval before being processed. For more information on Dual Authorisation, please discuss with your Account Manager.|
|`APPROVAL_REJECTED`|This status is applied where Dual Authorisation has been enabled for your organisation and the file approval has been declined by the approver user.|
|`ACCEPTED`|?? |
|`PARTIALLY_ACCEPTED`|?? |
|`COMPLETE`| The file has been successfully processed; all transactions have passed validation.|
|`COMPLETE_WITH_ERRORS`|Initial validations carried out on the file have resulted in some transactions being rejected while others have been successfully validated.|
|`IN_PROGRESS`|The file is currently being processed; in this status, the initial validations on the file are pending.|
|`REJECTED`| There was an issue with the file; the initial validations on the transactions within the file failed and it has been rejected.|
|`REVOKED`|While still an `IMPORT` file, the transactions in the file have been revoked. The transactions will not be passed to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.csm}}">Clearing</a> for processing. |
|`PARTIALLY_REVOKED`|Some transactions within the file have been revoked and will not be passed to Clearing for further processing,|
|`PENDING`|??|
|`PENDING_SETTLEMENT`|??|


{% include tip.html content= "This endpoint returns file details and not the actual file binary." type="primary" %}


{% include swagger_fm.html %}

{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-files-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listFilesUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
