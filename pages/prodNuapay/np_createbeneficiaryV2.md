---
title: Create Beneficiary
keywords: Create Beneficiary
summary: "Create Beneficiary API Request."
sidebar: ct_sidebar
permalink: np_createbeneficiaryV2.html
folder: prodNuapay
toc: false
---

## Overview

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %}

When working with this endpoint note that:

* Unlike the Direct Debit payment API, Beneficiary and CT requests do not require a Creditor Scheme ID or SUN reference.
* Before you can initiate a payment via the Create Credit Transfer request you must first create a beneficiary.
* Alternatively it is possible to generate a new beneficiary and a payment in a single request. See the <a href ="np_createctandbene.html">Create Credit Transfer and Beneficiary</a> request.



## API Versions

<!--TAB NAMES START-->
<ul id="profileTabs" class="nav nav-tabs">
    <li class="active"><a href="#profile" data-toggle="tab">V2 - Asynchronous</a></li>
    <li><a href="#about" data-toggle="tab">V1 - Synronous</a></li>
</ul>
<!--TAB NAMES END-->

<div class="tab-content"> <!--START Div for both Tabs -->

<div role="tabpanel" class="tab-pane active" id="profile"> <!--START Div Tab1 -->

Version 2

<ul id="profileTabs3" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs3', 'https://sentenial.github.io/credit-transfers/docs/redoc-v2.html');
var timerRef3 = setInterval(function() { getDocs('operation/addBeneficiaryUsingPOST','#profileTabs3',timerRef3); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>



</div> <!-- END for Div Role tabpanel-->

<div role="tabpanel" class="tab-pane" id="about"> <!--START Div Tab2 -->

Version 1


<ul id="profileTabs2" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs2', 'https://sentenial.github.io/credit-transfers/docs/redoc.html');
loadRedoc2('#profileTabs2', 'https://sentenial.github.io/credit-transfers/docs/redoc-v2.html');

<!--var timerRef = setInterval(function() { getDocs('operation/addBeneficiaryUsingPOST','#profileTabs2',timerRef); }, 500);-->


</script>


<div id="mydiv2"></div>
</div>
</div>







</div> <!-- END for Div Role tabpanel-->
</div> <!--END Div for both Tabs -->


{% include links.html %}
