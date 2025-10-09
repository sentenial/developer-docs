---
title: List Verifications
keywords: List Verifications
summary: "List Verification RESTful API"
sidebar: ver_sidebar
permalink: ver_listverification.html
folder: prodNuapay
toc: false
---

## API Details

The List Verification request allows you to:

* View a collection verification requests
* Specify a range be setting the `fromdatetime` and the `todatetime`.
* Check the `status`
* Retrieve an `id` to [Retrieve Cerification](ver_retrieveverification.html)
* Pass a `name` to retrieve specific verifications.


{% include idempotency.html %}


{% include swagger_ver.html %}

{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/verification-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getVerificationListUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
