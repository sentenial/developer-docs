---
title: Create Certificates
keywords: Create Certificate API
summary: "Create Certificate RESTful API"
sidebar: sec_sidebar
permalink: np_seccreatecert.html
folder: prodSecurity
toc: false
---

## API Details

The Create Certificate request allows you to create a certificate for JWS or for MTLS.

{% include tip.html content="You can have up to **two certificates** at a time. This lets you keep one active while setting up a new one, making it easier to transition before the old certificate expires." %}

{% include swagger_gk.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/generateUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
