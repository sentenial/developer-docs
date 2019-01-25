---
title: Update/Delete Webhook
keywords: Update/Delete Open Banking Webhook
summary: "Update/Delete Open Banking Webhooks"
sidebar: ob_sidebar
permalink: ob_whrestupdel.html
folder: prodOpenBanking
toc: true
---

## API Details 

Webhooks may be updated (using the `PUT` method) or deleted (using the `DELETE` method)  as required when you pass the Webhook identifier in the required request.


<ul id="profileTabs" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/webhooks-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/updateWebhookUsingPUT','#profileTabs',timerRef); }, 500);
</script>
</div>
</div>



<ul id="profileTabs2" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef2 = setInterval(function() { getDocs('operation/deleteWebhookUsingDELETE','#profileTabs2',timerRef2); }, 500);
</script>
</div>
</div>


{% include links.html %}
