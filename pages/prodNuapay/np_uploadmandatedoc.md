---
title: Upload Mandate Document
keywords: Upload Mandate Document API
summary: "Upload Mandate Document RESTful API"
sidebar: np_sidebar
permalink: np_uploademandatedoc.html
folder: prodNuapay
toc: false
---

## API Details

If you want to upload a representation of the mandate, for example if you have a signed paper mandate, have scanned it and saved it as a PDF, you can upload this to Nuapay so that it is linked to the required mandate.

This can then be viewed later if you use the <a href = "np_retrievemandatedoc.html"> Retrieve Mandate Document</a> call.

{% include swagger_np.html %}

{% include urls.html %}


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
