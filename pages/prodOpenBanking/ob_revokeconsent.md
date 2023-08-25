---
title: Revoke Consent
keywords: Revoke Open Banking AIS Consent
summary: "Revoke Open Banking Consent RESTful API"
sidebar: ob_sidebar
permalink: ob_revokeconsent.html
folder: prodOpenBanking
toc: false
---

## API Details

Use the `consentId` returned in the [Create Consent](ob_createconsent.html) request to revoke the Consent.


{% include swagger_ob_ais.html %}

{% include urls-ob.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

 {% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger-ais/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/revokeAccountConsentUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
