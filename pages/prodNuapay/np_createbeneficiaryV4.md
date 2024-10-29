---
title: Create Beneficiary
keywords: Create Beneficiary
summary: "Create Beneficiary RESTful API"
sidebar: ct_sidebar
permalink: np_createbeneficiaryV4.html
folder: prodNuapay
toc: false
---

<p>Summary: Create Beneficiary RESTful API</p>

<ul id="versionTabs" class="nav nav-tabs">
    <li class="active"><a href="#v2" data-toggle="tab">V2</a></li>
    <li><a href="#v1" data-toggle="tab">V1</a></li>
</ul>

<div class="tab-content">
    <div role="tabpanel" class="tab-pane active" id="v2">
        <h2>Version 2</h2>
        <div id="redoc-v2-container"></div>
    </div>
    <div role="tabpanel" class="tab-pane" id="v1">
        <h2>Version 1</h2>
        <div id="redoc-v1-container"></div>
    </div>
</div>

<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
<script type="text/javascript">
    function loadRedoc(version, containerId, redocUrl) {
        var iframe = document.createElement('iframe');
        iframe.src = redocUrl;
        iframe.width = '100%';
        iframe.height = '600px';
        iframe.style.border = 'none';
        document.getElementById(containerId).appendChild(iframe);

        iframe.onload = function() {
            this.style.height = this.contentWindow.document.body.scrollHeight + 'px';
        }
    }

    $(document).ready(function() {
        loadRedoc('v2', 'redoc-v2-container', 'https://sentenial.github.io/credit-transfers/docs/redoc-v2.html#operation/addBeneficiaryUsingPOST');
        loadRedoc('v1', 'redoc-v1-container', 'https://sentenial.github.io/credit-transfers/docs/redoc.html#operation/addBeneficiaryUsingPOST');

        $('#versionTabs a').click(function (e) {
            e.preventDefault();
            $(this).tab('show');
        });
    });
</script>

<style>
    .tab-content {
        border: 1px solid #ddd;
        border-top: none;
        padding: 15px;
    }
    .nav-tabs {
        margin-bottom: 0;
    }
</style>

{% include links.html %}
