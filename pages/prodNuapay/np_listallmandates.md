---
title: List Originator Mandates / DDIs
keywords: List all Mandates API per organization
summary: "List Mandates RESTful API returning all mandates/DDIs for a single organization"
sidebar: np_sidebar
permalink: np_listallmandates.html
folder: prodNuapay
toc: false
---

## API Details

This List Mandates request allows you to view a collection of mandates/DDIs linked to an individual originator. All mandates/DDIs *under all schemes* are returned.

{% include swagger_np.html %}

{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listOrganizationMandatesUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
