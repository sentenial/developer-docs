---
title: Upload Mandate / DDI Document
keywords: Upload Mandate Document API
summary: "Upload Mandate Document RESTful API"
sidebar: np_sidebar
permalink: np_uploademandatedoc.html
folder: prodNuapay
toc: false
---

## API Details

If you want to upload a representation of the mandate/DDI, for example if you have a signed paper mandate, have scanned it and saved it as a PDF, you can upload this to Nuapay so that it is linked to the required mandate/DDI.

This can then be viewed later if you use the [Retrieve Mandate Document](np_retrievemandatedoc.html) service.

{% include swagger_np.html %}

{% include urls.html %}
{% include tip.html content="You must use the resource identifier of the `schemeId` in your request and not the actual creditor scheme ID or SUN. This identifier will be similar to this: abxq9kq52l. Similarly, the mandate identifier is the resource identifier (e.g., rtsxq8kaby5) and is not the actual unique mandate reference - so in this case you would call POST /schemes/abxq9kq52l/mandates/rtsxq8kaby5/document" %}

{% include idempotency.html %} 

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/putPdfFileUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>




<!--{% include swaggerlink.html %}-->
