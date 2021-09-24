---
title: Retrieve Banks
keywords: Retrieve Banks Open Banking
summary: "Retrieve Bank RESTful API - use this service to retrieve the list of participating banks"
sidebar: ob_sidebar
permalink: ob_getbank.html
folder: prodOpenBanking
toc: false
---

## API Details

The Retrieve Bank service allows you to:
* Retrieve a list of the banks participating in Open Banking.
* Filter based on `supportedcurrencies` of the bank.

The participating ASPSPs are returned in order of popularity (dynamically determined based on Nuapay PSUs' preferences).

{% include tip.html content="Only one test bank (NUAPAY ASPSP OPENIDCONNECT) is available on the Sandbox environment." %}

|Where you specify two or more value for the `supportedcurrencies` array (in the Query Parameters of your request), the ASPSPs returned will support either currency; so the parameter is treated as a logical OR (not as an AND).|

## Bank Families

In some cases a single bank may have a number of regional banks linked to it.
* Use the `bankfamilyid` to filter for a specific bank family.
* Or use the `excludebankfamily` filter to only return those banks that do not have any linked regional banks.

For more on this see [View Bank Families](ob_getbankfamilies.html).

## Bank Metadata

This service also returns details on what the bank expects when interacting with it for PISP payments.

When working with Berlin Group banks, for example, the `PSU-ID` may be required to be passed; for some banks the creditor and debtor address information must be provided; others may have a limit on the minimum and maximum allowable payments, etc.

The service returns these details in the `bankMetaData` object, indicating if they are:

* `required`
* `optional`
* `not supported`

The following details are provided in a successful `200` response:

|debtorAddress|
|creditorAddress|
|remittanceInformation|
|psuId|
|customerIpAddress|
|minimumPaymentValue|
|maximumPaymentValue|

{% include swagger_ob.html %}


{% include urls-ob.html %}

## Retrieve Banks Endpoint

<ul id="profileTabs" class="nav nav-tabs">


</ul>

 {% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getBanksUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
