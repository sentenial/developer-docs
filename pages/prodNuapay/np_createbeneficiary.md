---
title: Create Beneficiary
keywords: Create Beneficiary
summary: "Create Beneficiary RESTful API"
sidebar: ct_sidebar
permalink: np_createbeneficiary.html
folder: prodNuapay
toc: true
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %}

When working with this endpoint note that:

* Unlike the Direct Debit payment API, Beneficiary and CT requests do not require a Creditor Scheme ID or SUN reference.
* Before you can initiate a payment via the Create Credit Transfer request you must first create a beneficiary.
* Alternatively it is possible to generate a new beneficiary and a payment in a single request. See the <a href ="np_createctandbene.html">Create Credit Transfer and Beneficiary</a> request.
* At its most basic, a beneficiary requires a name and a bank account reference. Additional data may also be stored but is not mandatory (address details and contact details, for example).
* If you specify domestic account details for a GBP beneficiary account, specify the Sort Code in `domesticBranchCode` (**do not use** `domesticBankCode`).

{% include idempotency.html %}

## Managing Address Details in SEPA

The European Payments Council, which manages SEPA rules, has specific guidelines for how addresses should be used when provided. Please review the following points to understand the specific requirements.

**If either you or your beneficiary is located outside the EEA**, you **must** provide countrparty address information, including:  
  - `line1` or `streetName`
  - `town`  
  - `country`  
This requirement comes from the **Wire Transfer Regulation (WTR)**, an EU law designed to ensure that banks and payment providers can identify the sender of a transfer. Providing these address details helps track payments and prevent fraud, money laundering, and other financial crime.

**If both you and your beneficiary are located within the EEA**, providing an address for your payee is **not mandatory**.  

**If you choose to provide an address voluntarily** (even when not required), at a minimum you must include:  
  - `town`  
  - `country`  

{% include swagger_ct.html %}

{% include urls.html %}

{% include async_note.html %}

<!-- TABS FOR V! and V2 -->

<div class="api-docs">
  <ul id="profileTabs" class="nav nav-tabs">
    <li><a href="#V2" data-toggle="tab">V2 Asynchronous</a></li>
    <li><a href="#V1" data-toggle="tab">V1 Synchronous</a></li>
  </ul>

  <div class="tab-content">
    <div role="tabpanel" class="tab-pane" id="V2">
      <!--  <p>Version 2 Add text here if required </p> -->
      <div id="V2-content"></div>
    </div>
    <div role="tabpanel" class="tab-pane" id="V1">
    <!--  <p>Version 1 Add text here if required </p> -->
      <div id="V1-content"></div>
    </div>
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
    $("#docs-jekyll").load(remoteDocs);
}

function unloadRedoc() {
    document.getElementById("docs-jekyll").remove();
}

function insertDocs(contentId, locationSelector) {
    const div = document.getElementById(contentId);
    if (div) {
        div.removeAttribute('id');
        $(locationSelector).html(div);
    }
}

function loadV1Docs() {
    loadRedoc('https://sentenial.github.io/credit-transfers/docs/redoc.html');
    setTimeout(function() {
        insertDocs('operation/addBeneficiaryUsingPOST', '#V1-content');
        unloadRedoc();
    }, 1000);
}

function loadV2Docs() {
    loadRedoc('https://sentenial.github.io/credit-transfers/docs/redoc-v2.html');
    setTimeout(function() {
        insertDocs('operation/addBeneficiaryUsingPOST', '#V2-content');
        unloadRedoc();
    }, 1000);
}

function setActiveTab(tabId) {
    $('#profileTabs a[href="#' + tabId + '"]').tab('show');
    localStorage.setItem('activeTab', tabId);
}

$(document).ready(function() {
    var activeTab = localStorage.getItem('activeTab') || 'V2';

    setActiveTab(activeTab);

    if (activeTab === 'V1') {
        loadV1Docs();
    } else {
        loadV2Docs();
    }

    $('#profileTabs a').on('shown.bs.tab', function(e) {
        var target = $(e.target).attr("href").substr(1);
        setActiveTab(target);

        if (target === "V1" && $('#V1-content').is(':empty')) {
            loadV1Docs();
        } else if (target === "V2" && $('#V2-content').is(':empty')) {
            loadV2Docs();
        }
    });
});
</script>
