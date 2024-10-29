---
title: Delete Certificate
keywords: Delete Certificate API
summary: "Delete Certificat RESTful API"
sidebar: sec_sidebar
permalink: np_secdeletecert.html
folder: prodSecurity
toc: false
---

## API Details

The Delete Certificate request allows you to delete your Certificates.

{% include warning.html content="Deleting a certificate cannot be undone: proceed with caution!" type="primary" %}


{% include swagger_gk.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/gatekeeper-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/deleteUsingDELETE','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
