---
title: File Upload
keywords: Upload CT/DD File
summary: "Use the Upload service to pass Credit Transfer and/or Direct Debit files via REST."
sidebar: fm_sidebar
permalink: fm_file_upload.html
folder: prodFileMgmt
---

Use the `POST /files` service to upload Credit Transfer or Direct Debit files.


{% include swagger_fm.html %}

{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-files-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/uploadFileUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
