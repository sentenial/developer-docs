---
title: Create Direct Debit & Mandate/DDI
keywords: Create Direct Debit & Mandate
summary: "Create Direct Debit & Mandate RESTful API - generate a mandate and a payment in a single API call."
sidebar: np_sidebar
permalink: np_createddandmand.html
folder: prodNuapay
toc: false
---

## API Details

As outlined in the [Create Direct Debit](np_createdirectdebit.html) service, you must have an `ACTIVE` mandate/DDI before you can begin to collect Direct Debit payments. Typically you would use the [Create Mandate](np_createmandate.html) endpoint and then reference the successfully activated mandate/DDI when you create the Direct Debit payment.

The **Create Direct Debit and Mandate** call allows you to combine these separate requests into a single call; the request performs two operations:

* A mandate/DDI is created in `ACTIVE` status
* A Direct Debit payment is created and linked to the new mandate/DDI


{% include note.html content="A successful request will result in a new mandate and direct debit being created. If the request is unsuccessful neither a mandate/DDI nor a direct debit will be created." %}


The Create Direct Debit and Mandate request must include:

* A requested <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.collection_date}}">collection date</a> for the Direct Debit payment
* The payment amount
* The payer's name
* The payer's account details
* The Merchant's Nuapay IBAN

{% include idempotency.html %}


{% include tip.html content="In Bacs, because the DDI will need to be registered with the scheme (via an AUDDIS submission) before the first Direct Debit payment can be made, if the `requestedCollectionDate` is not set beyond the 3 business days into the future, the date will be automatically shifted." %}


{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addSinglePaymentMOTFUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
