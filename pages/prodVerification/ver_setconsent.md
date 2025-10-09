<!-- NOT INCLUDED AS IT'SMORE AN INTERNAL SERVICE
---
title: Set Consent
keywords: Patch Consent
summary: "Set Consent RESTful API"
sidebar: ver_sidebar
permalink: ver_setconsent.html
folder: prodNuapay
toc: false
---

## API Details

This endpoint records the **user’s final decision** regarding an Account Verification (VOP/COP) attempt.  
It updates the verification record in the backend with the explicit action the user took after reviewing the verification results (e.g. *Match*, *Partial Match*, *No Match*).


### When to Call This Endpoint
Call this endpoint **immediately after** the end user has interacted with the Account Verification UI and made a final decision — either to proceed or to cancel.  

Typical use cases include:
- **Add/Edit Beneficiary** – When the user creates or modifies a beneficiary profile.  
- **Create Credit Transfer (CT)** – When a verification check is completed before a payment is initiated.  

> The `verificationId` used in the request path must match the identifier returned in the `uri` field of the initial `POST /verifications` response.

### Example Workflow

1. `POST /verifications` → Initiate verification.
1. User reviews match results in the UI and makes a decision.
1. `PATCH /verifications/{verificationId}` → Record user’s final choice.
1. `GET /verifications/{verificationId}` → Retrieve decision for downstream processing.


{% include idempotency.html %}


{% include swagger_ver.html %}

{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/verification-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/setDetailsForVerificationUsingPATCH','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}

-->