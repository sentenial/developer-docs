---
title: Retrieve Transactions in a Batch
keywords: Retrieve Transactions in a Batch
summary: "Use this service to retrieve all the transactions within a single batch."
sidebar: fm_sidebar
permalink: fm_retrieve_batch_tx.html
folder: prodFileMgmt
---
To retrieve all the transactions linked to a specific batch:

* Call the [Retrieve Batches](fm_retrieve_batches.html) (or the [Retrieve a Single File](fm_retrieve_single_batch.html) service).
* Get the file `Id` (Batch ID) returned in the 200 response.
* Pass this file `Id` and the Batch ID in this endpoint.

The response will provide 1-n transactions within the specified BATCH, including the:

* `amount`
* `currency`
* `endToEndId` (the unique transaction identifier)

In addition, depending on the file type, details of the Direct Debit or Credit Transfer, payer/payee are provided:

## Direct Debit Transaction Details

For `DIRECT DEBIT` transactions, the following **payer** details are returned:

* Name (`debtorName`)
* Mandate ID (`mandateReference`)
* IBAN (`debtorIBAN`)
* Settlement/Collection Date (`requestedCollectionDate`)

## Credit Transfer Transaction Details

For `CREDIT TRANSFER` transactions, the following **payee** details are returned:

* Name (`beneficiaryName`)
* IBAN (`beneficiaryIBAN`)
* Execution Date (`requestedExecutionDate`)

{% include swagger_fm.html %}

{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-files-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listTransactionsForBatchUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
