---
title: List Collective Account Postings
keywords: List Collective Account Posting
summary: "List Collective Account RESTful API"
sidebar: acc_sidebar
permalink: np_listcollaccountposts.html
folder: prodNuapay
toc: true
---

## API Details

Use this service to list all the postings (credits and debits) on a specific Collective Account (`collectiveAccountId`).

{% include swagger_pa.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/posting-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listCollectiveAccountPostingsUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
