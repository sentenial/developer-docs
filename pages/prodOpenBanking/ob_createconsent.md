---
title: Create Consent
keywords: Create Consent
summary: "Create Open Banking Consent API"
sidebar: ob_sidebar
permalink: ob_createconsent.html
folder: prodOpenBanking
toc: true
---

## API Details

Before making any account access request, the end user must first provide consent to that access. The Create Consent service allows you to create that initial user consent.

The Create Consent service:

* Allows you to initiate the Account Access request.
* You must specify the `accessPermissions` that are required. Note that currently only `ACCOUNT_DETAILS_READ` is supported.

## Create Consent Endpoint


{% include swagger_ob_ais.html %}

{% include urls-ob.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger-ais/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/createAccountConsentUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
