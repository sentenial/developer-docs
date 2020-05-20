---
title: List Direct Debits
keywords: List Direct Debits API
summary: "List Direct Debits RESTful API"
sidebar: np_sidebar
permalink: np_listdirectdebits.html
folder: prodNuapay
toc: true
---

## API Details

The List Direct Debits request allows you to view a collection of direct debits linked to:

* A Mandate/DDI
* A Specific Scheme
* All schemes (i.e. all payments)


{% include swagger_np.html %}

{% include urls.html %}

## List DDs Linked to a Mandate

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listDirectDebitsSchemeMandateUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

## List DDs Linked to a Scheme


<ul id="profileTabs2" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef2 = setInterval(function() { getDocs('operation/listDirectDebitsSchemeUsingGET','#profileTabs2',timerRef2); }, 500);
</script>
</div>
</div>


## List DDs Linked to an Originator (all payments)

<ul id="profileTabs3" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}

var timerRef3 = setInterval(function() { getDocs('operation/listDirectDebitsOrganizationUsingGET','#profileTabs3',timerRef3); }, 500);
</script>
</div>
</div>


{% include links.html %}
