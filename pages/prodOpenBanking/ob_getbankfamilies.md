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

In <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.stet}}">STET</a> and <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.berlin-group}}">Berlin Group</a>:

* Some <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSPs</a> are individually configured with a URL and token endpoint per regional bank.
* For example Credit Agricole in France (which follows the STET specification) has 44 distinct regional banks.
* Rendering individual regional banks on a user interface is problematic as, in the Credit Agricole example, this would result in 44 individual bank icons on the Bank Selection screen (with the user having to find his/her specific branch by scrolling though a large list).

To address this issue for `SELF-HOSTED` and `SELF-HOSTED-CALLBACK` users (who design their own UIs), Nuapay uses the concept of a “Bank Family”.

{% include tip.html content="A Bank Family is a bank that has numerous regional banks linked to it." %}

## Rendering Banks and Bank Families on the UI

{% include tip.html content="Rendering Bank Families on the UI, in the `SELF-HOSTED` integrations, is only required for EUR-based payments where banks are operating under the STET or Berlin Group specifications; GBP payments, processed under the OBIE standard, do not use bank families. " %}

For users, who have integrated in `SELF-HOSTED` or `SELF-HOSTED-CALLBACK` mode, that want to render both standalone banks and bank families (banks that have a number of linked branches) on the Bank selection screen, we recommend that you:

1. Call GET `/banks` (see [Retrieve Banks](ob_getbank.html)) to load all banks and cache the result. (This call returns all standalone banks and all bank branches).
1. Call GET `/bankfamilies` (see below) and cache the results. Where 10 banks branches are returned from the same bank (for example), these should be filtered out so that only one bank is shown on the Bank Selection page, rather than rendering the 10 individual branches on this screen.
1. The user can then select either a standalone Bank or a Bank that has associated branches.
1. If the user selects a bank with associated branches then render those branches (there is no extra REST call). In this case, use the cached GET `/banks` response and apply the `bankfamillyId` filter to render a bank branches drop-down list.
1. If the user selects a standalone bank, then no branch selection is required and the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> is redirected to his selected bank.

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
