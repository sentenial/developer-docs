---
title: Create Beneficiary
keywords: Create Beneficiary
summary: "Create Beneficiary API Request."
sidebar: ct_sidebar
permalink: np_createbeneficiaryV7.html
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

<!-- script-->

<script>

    function loadRedoc(remoteDocs) {
        jQuery('<div/>', {
            id: 'docs-jekyll',
            class: 'some-class',
            title: 'now this div has a title!'
        }).prependTo('body');
        $("#docs-jekyll").hide();
        $("#docs-jekyll").load( remoteDocs );
    }

    function unloadRedoc() {
        document.getElementById("docs-jekyll").remove();
    }

    function insertDocs(contentId, locationSelector) {
        const div = document.getElementById(contentId);
         //we want to remove the id as it can be picked up again otherwise
        // after selecting the docs by id we scrub them to not interfere with v3 loads
        // Select all elements inside the div
        div.removeAttribute('id');
        $(locationSelector).html(div);
    }

</script>

<!-- end script-->




<div class="tab-content"> <!--START Div for both Tabs -->


<div role="tabpanel" class="tab-pane active" id="V1"> <!--START Div Tab1 -->

Version 2

//load the v1 docs and insert where we want the docs to be
    setTimeout( function() { loadRedoc('https://sentenial.github.io/credit-transfers/docs/redoc.html');},0 );
    setTimeout(function() { insertDocs('operation/addCreditTransferUsingPOST','#V1'); }, 500);

    setTimeout( function() { unloadRedoc();},800 );


</div> <!-- END for Div Role tabpanel-->

<div role="tabpanel" class="tab-pane" id="V2"> <!--START Div Tab2 -->

Version 2


    setTimeout( function() { loadRedoc('https://sentenial.github.io/credit-transfers/docs/redoc-v2.html');},1000 );
    setTimeout(function() { insertDocs('operation/addCreditTransferV2UsingPOST','#V2'); }, 1500);

    setTimeout( function() { unloadRedoc();},2000 );





</div> <!-- END for Div Role tabpanel-->
</div> <!--END Div for both Tabs -->


{% include links.html %}
