---
title: Retrieve Mandate /DDI Document
keywords: Retrieve Mandate Document API
summary: "Retrieve Mandate Document RESTful API"
sidebar: np_sidebar
permalink: np_retrievemandatedoc.html
folder: prodNuapay
toc: false
---

## API Details

All Mandates/DDIs include a PDF representation of the mandate/DDI data. If required you may upload a different representation of a mandate (PDF, JPG and GIF formats are all supported).

The **Retrieve Mandate Document** call allows you to access the file representation of the mandate.

{% include swagger_np.html %}

{% include urls.html %}
{% include tip.html content="You must use the resource identifier of the `schemeId` in your request and not the actual creditor scheme ID or SUN. This identifier will be similar to this: abxq9kq52l. Similarly, the mandate identifier is the resource identifier (e.g., rtsxq8kaby5) and is not the actual unique mandate reference - so in this case you would call GET /schemes/abxq9kq52l/mandates/rtsxq8kaby5/document" %}



<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getPdfFileUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>



{% include links.html %}
