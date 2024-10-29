---
title: Create Beneficiary
keywords: Create Beneficiary
summary: "Create Beneficiary API Request."
sidebar: ct_sidebar
permalink: np_createbeneficiaryV8.html
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

<ul id="profileTabs" class="nav nav-tabs">
    <li class="active"><a href="#profile" data-toggle="tab">V2 Asynchronous</a></li>
    <li><a href="#about" data-toggle="tab">V1 Synchronous</a></li>

</ul>
  <div class="tab-content">
<div role="tabpanel" class="tab-pane active" id="V1">

Version 1

<script>
    //load the v1 docs and insert where we want the docs to be
    setTimeout( function() { loadRedoc('https://sentenial.github.io/credit-transfers/docs/redoc.html');},0 );
    setTimeout(function() { insertDocs('operation/addCreditTransferUsingPOST','#V1'); }, 500);

    setTimeout( function() { unloadRedoc();},800 );
</script>

</div>

<div role="tabpanel" class="tab-pane" id="V2">

Version 2

<script>
  //load the v2 docs and insert where we want the docs to be
  setTimeout( function() { loadRedoc('https://sentenial.github.io/credit-transfers/docs/redoc-v2.html');},1000 );
  setTimeout(function() { insertDocs('operation/addCreditTransferV2UsingPOST','#V2'); }, 1500);

  setTimeout( function() { unloadRedoc();},2000 );
</script>
</div>
</div>


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
