---
title: View Bank Families
keywords: Retrieve Banks Families
summary: "Retrieve Bank Families RESTful API - use this service to retrieve the list of bank families"
sidebar: ob_sidebar
permalink: ob_getbankfamilies.html
folder: prodOpenBanking
toc: false
---

## API Details

## Overview

In STET and Berlin Group:

* Some ASPSPs are individually configured with a URL and token endpoint per regional bank.
* For example Credit Agricole in France (STET) has 44 distinct regional banks.
* Rendering individual regional banks on a user interface is problematic as, in the Credit Agricole example, this would translate to 44 individual bank options.
* In practice this would mean 44 identical icons on a Bank Selection screen (with the PSU having to find his/her specific branch by scrolling though a large list).

To address this issue for `SELF-HOSTED` and `SELF-HOSTED-CALLBACK` users (who design their own UIs), Nuapay uses the concept of a “Bank Family”.

{% include tip.html content="A Bank Family is a bank that has numerous regional banks linked to it." %}

{% include swagger_ob.html %}


{% include urls-ob.html %}


## View Bank Families Endpoint

<ul id="profileTabs" class="nav nav-tabs">


</ul>

 {% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getBankFamiliesUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
