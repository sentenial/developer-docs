---
title: List Organisations
keywords: List Organisations
summary: "The List Organisation RESTful API allows you to retrieve details of the organisations under your partner entity, including the encoded Organisation identifier, which is used to retrieve tokens."
sidebar: tok_sidebar
permalink: tok_listorgs.html
folder: prodTokenMgmt
toc: true
---

## API Details

For **Partner** users, use the List Organisation Endpoint to retrieve the details of all your child organisations, including their unique identifiers:



{% include swagger_org.html %}

{% include urls-ob.html %}


<ul id="profileTabs1" class="nav nav-tabs">
</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/organisation-swagger/docs/redoc.html');   
var timerRef1 = setInterval(function() { getDocs('operation/listChildOrganisationsUsingGET','#profileTabs1',timerRef1); }, 500);
</script>
</div>
</div>
