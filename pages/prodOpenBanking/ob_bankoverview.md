---
title: Bank Overview
keywords: Open Banking Participating Banks Overview
summary: "The Bank APIs allow you to retrieve and view details of all available banks (ASPSPs)"
sidebar: ob_sidebar
permalink: ob_bankoverview.html
folder: prodOpenBanking
toc: false
---

When making a payment, <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSUs</a> must initially select the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> with which their account is held.

* In [CHECKOUT](ob_pispimplementations.html#implementation-overview) and [REDIRECT](ob_pispimplementations.html#implementation-overview) modes the list of banks is displayed automatically.
* In [SELF-HOSTED](ob_pispimplementations.html#implementation-overview) and [SELF-HOSTED-CALLBACK](ob_pispimplementations.html#implementation-overview) mode, you will need to call [Retrieve Banks](ob_getbank.html) to get the list of banks that you want to display to your PSUs on your user interface.

Nuapay supports Open Banking payments in GBP and EUR currencies. Click the country link below to view the banks that are currently available on our Live environment.

## Country Coverage

<!--
<iframe src="https://coverage.nuapay.com/coverage/" width="100%" height="900" frameborder = "0" title="Coverage"></iframe>
-->


{% include map.html %}


Want a better view? <a href= "https://coverage.nuapay.com/coverage/" target = "new">Open the map in a new window/tab</a>

{% include note.html content="We are constantly building on our connections and currently we have approximately 95% bank coverage on average, in the countries referenced below." %}
