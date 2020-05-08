---
title: PISP Implementation Options
keywords: Open Banking PISP Implementation Options
summary: "Payment Initiation Service Provider Checkout Page implementation Options"
sidebar: ob_sidebar
permalink: ob_pispimplementations.html
folder: prodOpenBanking
---

Your PISP checkout page may be implemented in one of the following ways:

1. CHECKOUT
1. SELF_HOSTED
1. SELF_HOSTED_CALLBACK


|**Checkout**|This mode lets you use the Nuapay user interface for Bank Selection.|
|**Self-Hosted**| The user interface is handled by you, the merchant (or partner, acting on behalf of a merchant) for Bank Selection; callback handling is through the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a>.|
|**Self-Hosted-Callback**| In this mode the user interface is handled by you, the merchant (or partner, acting on behalf of a merchant) and you manage the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a>'s experience after interacting with an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>: the Callback bypasses the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a>, you manage the callback URL that is required for each <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> interaction|

{% include warning.html content="SELF_HOSTED_CALLBACK mode is currently only available in the Nuapay Test environment." %}


## What is the Best Approach? 

Each approach has its advantages and disadvantages - the table below summarises the different implementations  

|**Mode**|**Advantages**|**Disadvantages**|
|Checkout| Easier implementation; No bespoke UI design (e.g. for the Bank Selection screen) is required; No TPP license is required.|No UI customisation is possible; "Powered by Nuapay" is displayed on the UI.|
|Self-Hosted| Full control over the user interface | Requires more development effort; Requires a call to the List Bank service; following the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a>'s interaction on the selected <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>, the Callback URL redirects the user to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a>.| 
|Self-Hosted-Callback|Full control over the user interface and the Callback URL; it is possible to bypass the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a> application|Requires additional development effort; Requires a call to the List Bank service; Registration of the callback URL (via Software Statement Assertions in the UK Open Banking scheme, for example) at each <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> is required.|

Note too that it is possible to interact with the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.nupay_tpp}}">Nuapay TPP</a> as a merchant or as a partner. 

For more information on any of the various implementations, select from the options below:

|**Mode**|**Implementation**|
|Partner|[Checkout](ob_checkoutoverview.html)|
||[Self-Hosted](ob_selfsetupoverview.html)|
||[Self-Hosted-Callback](ob_selfcallbacksetupoverview.html)|
|Merchant|[Checkout](ob_checkoutoverviewmerch.html)|
||[Self-Hosted](ob_selfsetupoverviewmerch.html)|
||[Self-Hosted-Callback](ob_selfcallbackmerch.html)|







{% include links.html %}
