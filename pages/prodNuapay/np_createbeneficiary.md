---
title: Create Beneficiary
keywords: Create Beneficiary
summary: "Create Beneficiary RESTful API"
sidebar: np_sidebar
permalink: np_createbeneficiary.html
folder: prodNuapay
toc: false
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %}

When working with this endpoint note that:

* Unlike the Direct Debit payment API, Beneficiary and CT requests do not require a Creditor Scheme ID or SUN reference.
* Before you can initiate a payment via the Create Credit Transfer request you must first create a beneficiary.
* Alternatively it is possible to generate a new beneficiary and a payment in a single request. See the <a href ="np_createctandbene.html">Create Credit Transfer and Beneficiary</a> request.

{% include note.html content="at its most basic, a beneficiary requires a name and a bank account reference. Additional data may also be stored but is not mandatory (address details and contact details, for example)" %}

{% include tip.html content="If you specify domestic account details for the beneficiary account, specify the Sort Code in **domesticBranchCode** (not in the **domesticBankCode**)." %}

{% include idempotency.html %} 



{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addBeneficiaryUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
