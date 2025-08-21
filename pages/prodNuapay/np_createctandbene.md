---
title: Create Credit Transfer & Beneficiary
keywords: Create Credit Transfer & Beneficiary
summary: "Create Credit Transfer & Beneficiary RESTful API - generate a payment and its beneficiary in a single API call."
sidebar: ct_sidebar
permalink: np_createctandbene.html
folder: prodNuapay
toc: true
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %}

The Create Credit Transfer request requires that you have first created a beneficiary. In some scenarios it is simpler to generate both the beneficiary and the payment at the same time and this request allows you to do that.

{% include note.html content="If the beneficiary details you reference in the request have been previously provided (and that beneficiary is already stored against your merchant profile) Nuapay will reuse that stored beneficiary data: a new beneficiary is only created if his/her beneficiary account has not been referenced before in a previous Credit Transfer payment." %}

{% include idempotency.html %}

## SEPA Credit Transfers

When creating a SEPA Credit Transfer (also referred to as an SCT or CT) payments, note that:

* Payments are processed for **EUR currency payments only**
* CT payments, unlike Direct Debit payments, do not require that the transaction is passed to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing system</a> days in advance of the collection date.
* If you create your CT payment early enough on a specific working day (before 8AM GMT), the funds will typically be credited to your beneficiary on the same day.
* If you create the payment later in the day then the CT will generally be credited to the beneficiary on the following business day.

{% include important.html content="A Note on GMT: Nuapay apply Daylight Savings Time (DST) during the summer months (which is commonly referred to as British Summer Time (BST)). BST runs from the last Sunday in March to the last Sunday in October. During this period the cut off time is actually GMT -1 (so 07:00 GMT); during the period from November to the end of March, the cut off time is 08:00 GMT." type="primary" %}

## Faster Payments

The Faster Payments Scheme (FPS) is an instant payment scheme (with funds being credited to the beneficiary generally in a matter of seconds) available in the UK.
Note that FPS:

* Is available for **GBP curency payments only**.   
* Unlike SEPA CT, FPS is a 24/7/365 system.
* Requires the following values in your request:
  * `paymentCurrency` = GBP.
  * `type` = EXPRESS

{% include tip.html content="If you specify domestic account details for the beneficiary account, specify the Sort Code in **domesticBranchCode** (not in the **domesticBankCode**)." %}

## Payment Types

Payments can have a `type`:

* STANDARD
* EXPRESS
* FASTEST_POSSIBLE

|**Currency**|**Default Type**|**CT Type**|
|EUR|`STANDARD`| SCT |
|EUR|`EXPRESS` | SCT Instant|
|GBP|`STANDARD`| Bacs Direct Credit|
|GBP|`EXPRESS`| FPS|

By default EUR payments are processed as `STANDARD`; GBP payments are processed as `EXPRESS`.

{% include tip.html content="If you would like a different default configuration, please discuss your requirements with your account manager." %}

Where you specify `FASTEST_POSSIBLE` a payment will go via the the Express payment if possible (i.e. if configured for you); if it is not possible to send the payment as Express  then the transaction will be processed as a Standard payment.

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

{% include swagger_np.html %}

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
        insertDocs('operation/addCTBeneficiaryOnFlyUsingPOST', '#V1-content');
        unloadRedoc();
    }, 1000);
}

function loadV2Docs() {
    loadRedoc('https://sentenial.github.io/credit-transfers/docs/redoc-v2.html');
    setTimeout(function() {
        insertDocs('operation/addCTBeneficiaryOnFlyV2UsingPOST', '#V2-content');
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
