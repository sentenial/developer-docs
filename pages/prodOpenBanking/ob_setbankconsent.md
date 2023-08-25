---
title: Set Bank Consent
keywords: Set Bank AIS Consent
summary: "Set the required Bank ID for the Consent"
sidebar: ob_sidebar
permalink: ob_setbankconsent.html
folder: prodOpenBanking
toc: false
---

## API Details

For merchants who are integrating via the `SELF-HOSTED` or `SELF-HOSTED-CALLBACK` integration type, the generated consent must have a `bankId`. This allows the user to be directed to an appropriate bank, to give consent for the account access. This service allows you to append this value to the consent.

Once the consent is successfully patched, Nuapay <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.tpp}}">TPP</a> triggers the create consent request at the selected <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>.

When the consent creation is successful, the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> is redirected to authorise the consent.


{% include swagger_ob_ais.html %}

{% include urls-ob.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

 {% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger-ais/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/setBankIdForConsentUsingPATCH','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
