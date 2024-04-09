---
title: Retrieve Transactions
keywords: Retrieve Transactions in a File
summary: "Use this service to retrieve all the transactions within a specific file."
sidebar: fm_sidebar
permalink: fm_retrieve_all_tx.html
folder: prodFileMgmt
---
To retrieve all the transactions linked to a file:

* Call the [Retrieve Files](fm_retrieve_files.html) (or the [Retrieve a Single File](fm_retrieve_single_file.html) service).
* Get the file `Id` returned in the 200 response.
* Pass this unique batch identifier in this endpoint.

The response will provide 1-n transactions within the specified file, including the:

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
var timerRef = setInterval(function() { getDocs('operation/listTransactionsForFileUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
