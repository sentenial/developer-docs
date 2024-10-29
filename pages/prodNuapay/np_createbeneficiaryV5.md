---
title: Create Beneficiary
keywords: Create Beneficiary
summary: "Create Beneficiary RESTful API"
sidebar: ct_sidebar
permalink: np_createbeneficiaryV5.html
folder: prodNuapay
toc: false
---

<div>
  <!-- Headline for common explanations -->
  <h2>View Beneficiary API</h2>
  <p>Here is the detailed documentation for the 'View Beneficiary' endpoint for both versions of the API.</p>

  <!-- Section for API V1 -->
  <div>
    <h3>API V1</h3>
    <div id="redoc-container-v1"></div> <!-- Container for V1 -->
  </div>

  <!-- Section for API V2 -->
  <div>
    <h3>API V2</h3>
    <div id="redoc-container-v2"></div> <!-- Container for V2 -->
  </div>

  <!-- Redoc Script to load specific endpoints -->
  <script src="https://cdn.redoc.ly/redoc/latest/bundles/redoc.standalone.js"></script>

<div>
  <!-- Section for API V1 -->
  <div>
    <h3>API V1 - Add Beneficiary</h3>
    <div id="redoc-container-v1"></div> <!-- Container for V1 -->
  </div>

  <!-- Section for API V2 -->
  <div>
    <h3>API V2 - Add Beneficiary</h3>
    <div id="redoc-container-v2"></div> <!-- Container for V2 -->
  </div>
</div>

<script type="text/javascript">
  // Function to load Redoc and scroll to the specific endpoint
  function loadAndScrollToEndpoint(redocUrl, containerId, operationId) {
    Redoc.init(redocUrl, {
      scrollYOffset: 50,
      hideDownloadButton: true,
      requiredPropsFirst: true,
      hideSingleRequestSampleTab: true
    }, document.getElementById(containerId)).then(function() {
      // Scroll to the specific operation after Redoc is initialized
      setTimeout(function() {
        var operationElement = document.querySelector('a[href="#operation/' + operationId + '"]');
        if (operationElement) {
          operationElement.scrollIntoView();
        }
      }, 1000);  // Delay to ensure Redoc has fully rendered
    });
  }

  // Load and scroll to 'addBeneficiaryUsingPOST' in V1
  loadAndScrollToEndpoint('https://raw.githubusercontent.com/sentenial/credit-transfers/main/v1-credit-transfers.yaml', 'redoc-container-v1', 'addBeneficiaryUsingPOST');

  // Load and scroll to 'addBeneficiaryUsingPOST' in V2
  loadAndScrollToEndpoint('https://raw.githubusercontent.com/sentenial/credit-transfers/main/v2-credit-transfers.yaml', 'redoc-container-v2', 'addBeneficiaryUsingPOST');
</script>

</div>
