---
title: List Direct Debit Creditor Schemes
keywords: List Creditor Schemes API
summary: "List Creditor Schemes RESTful API"
sidebar: np_sidebar
permalink: np_listcredscheme.html
folder: prodNuapay
toc: false
---

## API Details

A payment scheme is a set of rules that govern how transactions are processed. SEPA and Bacs are two such schemes, which govern both Direct Debit and Credit Transfer transactions in the EU and in the UK.

* All mandates/DDIs that you create (and all subsequent Direct Debit payments) must be linked to a unique Creditor Scheme Identifier (CSID) for SEPA payments or to a Service User Number (SUN) for Bacs payments. 
* If you already have a CSID/SUN you will need to use List Creditor Schemes to retrieve its Nuapay resource identifier.

{% include note.html content="You must use the resource identifier of the scheme in your requests. This identifier will be similar to this: **abxq9kq52l** do not reference the actual creditor scheme ID or SUN in your requests." %}

If you lose this reference or if you have multiple CSIDs or SUNs and want to review them all, you can use the List Creditor Schemes service. You will use this resource identifier CSID/SUN in all subsequent Mandate and Direct Debit requests.


{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listCreditorSchemesUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}

