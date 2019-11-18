---
title: Activate Mandate
keywords: sample
summary: "Activate Mandate RESTful API"
sidebar: np_sidebar
permalink: np_activatemandate.html
folder: prodNuapay
toc: false
---

## API Details

<p>Where a mandate is in Pending or Suspended <a href="np_mandatestatuses.html">status</a> you can set it to Active so that Direct Debit Payments can be made against it.</p>

<p>If you are using paper mandates then you may need to consider an option on your custom application to allow operators to click a button to activate mandates when a signed mandate is received, which would call this request.</p>

<p>If you are using E-Mandates, the activate mandate request is dynamically called and may (optionally) include details related to the electronic signing event (IP Address, location of the signature, the mobile phone or email address used)</p>


{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/activateMandateUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
