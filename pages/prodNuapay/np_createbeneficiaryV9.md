---
title: Create Beneficiary
keywords: Create Beneficiary
summary: "Create Beneficiary API Request."
sidebar: ct_sidebar
permalink: np_createbeneficiaryV9.html
folder: prodNuapay
toc: false
---

<h1>API Documentation</h1>

### API Documentation

# Credit Transfers

## Create Beneficiary

> Summary: Create Beneficiary API Request.

### API Documentation

<div class="api-docs">
  <ul id="profileTabs" class="nav nav-tabs">
    <li><a href="#V2" data-toggle="tab">V2 Asynchronous</a></li>
    <li><a href="#V1" data-toggle="tab">V1 Synchronous</a></li>
  </ul>

  <div class="tab-content">
    <div role="tabpanel" class="tab-pane" id="V2">
      <h4>Version 2</h4>
      <div id="V2-content"></div>
    </div>
    <div role="tabpanel" class="tab-pane" id="V1">
      <h4>Version 1</h4>
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
        insertDocs('operation/addCreditTransferUsingPOST', '#V1-content');
        unloadRedoc();
    }, 1000);
}

function loadV2Docs() {
    loadRedoc('https://sentenial.github.io/credit-transfers/docs/redoc-v2.html');
    setTimeout(function() {
        insertDocs('operation/addCreditTransferV2UsingPOST', '#V2-content');
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