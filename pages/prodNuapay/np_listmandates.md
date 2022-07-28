---
title: List Mandates / DDIs
keywords: List Mandates API
summary: "List Mandates RESTful API"
sidebar: np_sidebar
permalink: np_listmandates.html
folder: prodNuapay
toc: false
---

## API Details

The List Mandates request allows you to view a collection of mandates/DDIs linked to a:

* Specific Scheme
* All schemes (i.e. all mandates)

Use an appropriate URI (as described below) to return the required collection of Mandates/DDIs.

{% include swagger_np.html %}

{% include urls.html %}
{% include tip.html content="You must use the resource identifier of the `schemeId` in your request and not the actual creditor scheme ID or SUN. This identifier will be similar to this: abxq9kq52l - so in this case you would call GET /schemes/abxq9kq52l/mandates. See [List Schemes](np_listcredscheme.html) for more on this." %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listSchemeMandatesUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
