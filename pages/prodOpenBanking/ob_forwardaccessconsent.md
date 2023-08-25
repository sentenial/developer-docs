---
title: Forward Accounts Access Consent Callback
keywords: Forward Accounts Access Consent Callback
summary: "Use this service to pass the consent callback to the Nuapay TPP"
sidebar: ob_sidebar
permalink: ob_forwardaccessconsent.html
folder: prodOpenBanking
toc: false
---

## API Details

This endpoint is required for the `SELF-HOSTED-CALLBACK` integration type.

In the consent flow:
* Call [Create Consent](ob_createconsent.html); this returns a `consentId` and the `aspspAuthURL`
* The PSU is redirected to the ASPSP Authentication URL.
* The user logs on and provides consent at the ASPSP and is redirected to the `callbackURL`.
* The consent callback is passed (forwarded) to the Nuapay TPP.
* The Nuapay TPP then polls the ASPSP for an Active consent.

Once the consent is successfully patched, Nuapay <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.tpp}}">TPP</a> triggers the create consent request at the selected <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>.

When the consent creation is successful, the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> is redirected to authorise the consent.


{% include swagger_ob_ais.html %}

{% include urls-ob.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

 {% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger-ais/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/forwardAccountAccessConsentCallbackPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
