---
title: Request Verification
keywords: Create Verification Request
summary: "Request Verification RESTful API"
sidebar: ver_sidebar
permalink: ver_reqverification.html
folder: prodNuapay
toc: false
---

## API Details

The Request Verification endpoint allows you to:

* Provide the `name` you want to verify.
* The name you provide will be compared to the account holder name stored at the bank.
* A successful request will result in a `201` verification created response. The verification is not completed at this point; initially, the verification request will have a `PENDING` status.
* Note that the end user will complete the verification via the User Interface (as described in the [End User Experience](ver_psujourney.html)).
* It is possible to have the verification flow as a pop-up (`CHECKOUT` mode) or the screen may be opened in a new browser Window/tab (`REDIRECT`); specify the required UI by setting the `integrationType` value.

{% include idempotency.html %}


{% include swagger_np.html %}

{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/verification-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/verifyUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
