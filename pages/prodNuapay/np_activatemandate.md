---
title: Activate Mandate / DDI
keywords: sample
summary: "Activate Mandate RESTful API"
sidebar: np_sidebar
permalink: np_activatemandate.html
folder: prodNuapay
toc: false
---

## API Details

Where a SEPA mandate is in `PENDING` or `SUSPENDED` [status](np_mandatestatuses.html) you can set it to `ACTIVE` so that Direct Debit Payments can be made against it.

* If you are using paper mandates then you may need to consider an option on your custom application to allow operators to click a button to activate mandates when a signed mandate is received, which would call this service.
* If you are using E-Mandates, the activate mandate request is dynamically called and may (optionally) include details related to the electronic signing event (IP Address, location of the signature, the mobile phone or email address used).


{% include tip.html content="Bacs DDIs must go through the Bacs automated registration process (AUDDIS) and are automatically set to `ACTIVE` in Nuapay, once successfully registered with payers' banks." %}


{% include swagger_np.html %}

{% include urls.html %}
{% include tip.html content="You must use the resource identifier of the `schemeId` in your request and not the actual creditor scheme ID or SUN. This identifier will be similar to this: abxq9kq52l. Similarly, the mandate identifier is the resource identifier (e.g., rtsxq8kaby5) and is not the actual unique mandate reference - so in this case you would call POST /schemes/abxq9kq52l/mandates/rtsxq8kaby5/activate" %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/activateMandateUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
