---
title: List Failed Direct Debits
keywords: List Failed Direct Debits API
summary: "List Failed Direct Debits RESTful API"
sidebar: np_sidebar
permalink: np_listfaileddds.html
folder: prodNuapay
toc: false
---

## API Details

Direct Debit payments can fail at various stages in their lifecycle.

Where you are creating payments via the API you will be informed in your API response when there is an error in your request. 

The List Failed Direct Debits API allows you to query any Bank-related rejects (i.e. any R-Transactions received after your DD payments have been exported to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing</a> or to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.bacs-clearing}}">Bacs</a>). 

It also allows you to list any Technical Rejects that you may have had (you will only have Technical Rejects if you are importing payments via file upload; API requests do not result in Technical Rejects).

Failed payments can be grouped into three basic types:

| Type | Description |
|-------|--------|
|Technical Rejects | If you are importing payments into Nuapay via a file upload, some payments may be rejected for failing business validation rules. You may receive a DD001 code, for example, if you reference a mandate/DDI that does not exist. Note that there are no Technical Rejects for API or UI-based payments. In the case of an API request the response will indicate in real time that the payment has failed (if you have provided an incorrect mandate or DDI reference in your Create Direct Debit call, for example, you will receive a 7021 error code). |
| Pre-settlement Failures | Payments that are created and exported that the Payer's bank then rejects or refuses before the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.collection_date}}">collection date</a>. Only applicable to SEPA schemes.|
| Post-settlement Failures	 | Payments that are exported and accepted but the bank then fails after the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.collection_date}}">collection date</a>. |

## API Details

The List Failed Direct Debits request allows you to return a list of all: 
* Technical rejects (only possible if you are processing files).
* Pre-settlement Rejects/Refusals (only in SEPA schemes).
* Post-settlement Returns/Refunds. 

We recommend that you schedule to run this request at various times in the lifecycle of your Direct Debits, to ensure that you have the current statuses of your payments before and after the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.collection_date}}">collection date</a>. 

Alternatively, you could implement a Webhook for <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.r-transaction}}">R-Transactions</a> (see details of the [Direct Debit R-Transaction](np_whddrejectevent.html) Webhooks for more).


{% include note.html content="Optionally you can use the technicalrejects boolean in your request. If technicalrejects is true then all Bank rejects and all technical rejects are returned; if set to false then only Bank rejects are returned." %}


{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listFailedDirectDebitUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
