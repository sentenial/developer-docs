---
title: Uploading a Contract
keywords: Uploading Contract Upload
summary: "Uploading a contract PDF is required as an initial step before combining it with a mandate."
sidebar: em_sidebar
permalink: em_contractupload.html
folder: prodEmandates
---

To upload a contract, use the <b>Upload Contract</b> request.


{% include note.html content="Contracts must be saved in PDF and we recommend that the file size does not exceed 1 MB." %}

You may use a `contractType` = OOFF or RCUR.

* Once-Off (OOFF) contracts are just used once in a single signing operation. 
* Recurring (RCUR) contracts can be re-used in multiple signing operations; this is useful where your business uses a standard contract and you want to offer all your customers the same PDF contract document.

{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 
 {% include redoc.html %}
 

 
loadRedoc('#profileTabs', 'https://sentenial.github.io/emandates-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/uploadContractPdfFileUsingPOST','#profileTabs',timerRef); }, 500);



</script>


<div id="mydiv"></div>


</div>
</div>


Once you have retrieved your contract identifier you can use it in your Prepare E-Mandate request in your chosen integration approach:

 

* <a href="em_tokenredirect.html">Redirect</a>
* <a href="em_token.html">Overlay</a>
* <a href="em_tokendirectapi.html">Direct API Integration</a>




<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/emandate-api/#upload-contract-document" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>




{% include links.html %}
