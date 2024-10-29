---
title: List Credit Transfers
keywords: List Credit Transfers API
summary: "List Credit Transfers RESTful API"
sidebar: ct_sidebar
permalink: np_listcts.html
folder: prodNuapay
toc: true
---

## API Details

The List Credit Transfers request allows you to view a collection of Credit Transfers linked to a:

* Single beneficiary
* All beneficiaries (under a single Originator)

Use an appropriate URI (as described below) to return the required array of CTs.

{% include swagger_np.html %}

{% include urls.html %}

## List CTs Linked to a Single Beneficiary

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
        insertDocs('operation/listCreditTransfersBeneficiaryUsingGET', '#V1-content');
        unloadRedoc();
    }, 1000);
}

function loadV2Docs() {
    loadRedoc('https://sentenial.github.io/credit-transfers/docs/redoc-v2.html');
    setTimeout(function() {
        insertDocs('operation/listCreditTransfersBeneficiaryUsingGET', '#V2-content');
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

## List ALL CTs (Linked to an Originator)

{% include async_note.html %}

<!-- TABS FOR V! and V2 -->

<div class="api-docs">
  <ul id="profileTabs" class="nav nav-tabs">
    <li><a href="#V21" data-toggle="tab">V21 Asynchronous</a></li>
    <li><a href="#V11" data-toggle="tab">V11 Synchronous</a></li>
  </ul>

  <div class="tab-content">
    <div role="tabpanel" class="tab-pane" id="V21">
      <!--  <p>Version 2 Add text here if required </p> -->
      <div id="V21-content"></div>
    </div>
    <div role="tabpanel" class="tab-pane" id="V11">
    <!--  <p>Version 1 Add text here if required </p> -->
      <div id="V11-content"></div>
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
        insertDocs('operation/listCreditTransfersUsingGET', '#V11-content');
        unloadRedoc();
    }, 1000);
}

function loadV2Docs() {
    loadRedoc('https://sentenial.github.io/credit-transfers/docs/redoc-v2.html');
    setTimeout(function() {
        insertDocs('operation/listCreditTransfersUsingGET', '#V21-content');
        unloadRedoc();
    }, 1000);
}

function setActiveTab(tabId) {
    $('#profileTabs a[href="#' + tabId + '"]').tab('show');
    localStorage.setItem('activeTab', tabId);
}

$(document).ready(function() {
    var activeTab = localStorage.getItem('activeTab') || 'V21';

    setActiveTab(activeTab);

    if (activeTab === 'V11') {
        loadV1Docs();
    } else {
        loadV2Docs();
    }

    $('#profileTabs a').on('shown.bs.tab', function(e) {
        var target = $(e.target).attr("href").substr(1);
        setActiveTab(target);

        if (target === "V11" && $('#V11-content').is(':empty')) {
            loadV1Docs();
        } else if (target === "V21" && $('#V21-content').is(':empty')) {
            loadV2Docs();
        }
    });
});
</script>
