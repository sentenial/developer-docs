---
title: Retrieve Organisation
keywords: Retrieve Organisation
summary: "Retrieve details of a specific organisation."
sidebar: tok_sidebar
permalink: tok_retrieveorg.html
folder: prodTokenMgmt
toc: true
---

## API Details

Use this endpoint to retrieve the details of a specific organisation. You must pass the `organisationId` (use the [List Organisations](tok_listorgs.html) to retrieve this unique identifier).

{% include swagger_org.html %}

{% include urls-ob.html %}

Use this service if you are a `partner` who wants to retrieve the details on your _child_ organisations, which exists under your partner.

<ul id="profileTabs1" class="nav nav-tabs">
</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/organisation-swagger/docs/redoc.html');   
var timerRef1 = setInterval(function() { getDocs('operation/retrieveOrganisationUsingGET','#profileTabs1',timerRef1); }, 500);
</script>
</div>
</div>
