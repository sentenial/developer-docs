---
title: Validate IBAN
keywords: SEPA Instant CT Validate IBAN
summary: "Validate Beneficiary IBAN for Incoming Inst SCT RESTful API"
sidebar: ip_sidebar
permalink: ip_validateiban.html
folder: prodInstantPayments
toc: false
---

As Origix IP has no visibility of the accounts held by your financial institution, the system:

* Makes an API request to an Endpoint <b>configured by your bank/financial institution</b> to validate the provided beneficiary account.
* This configured Endpoint will need to consume the Origix IP requests and respond to them appropriately.
* If the account is valid and can receive the SCT Inst payment then the Endpoint should respond to Origix IP with a ``200`` response code.
* Where the response to the Origix IP request is a ``400 - Account is invalid`` (or a ``500 - Server could not process the request``), the payment will be rejected; a REJECT notification will be dispatched from Origix IP to the CSM.

Accounts may fail validation for various reasons. For a table listing the possible return codes, expand the ``400 Account is invalid`` link from the API Responses section below.

## API Details

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/account-validation-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/PostValidatePaymentsUsingPOST','#profileTabs',timerRef); }, 500);

</script>


</div>



</div>

{% include links.html %}
