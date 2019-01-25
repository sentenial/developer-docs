---
title: List Webhooks
keywords: List Open Banking Webhook
summary: "List Open Banking Webhooks"
sidebar: ob_sidebar
permalink: ob_whrestlist.html
folder: prodOpenBanking
toc: false
---

## API Details 

The List service will return an array of configured Webhooks linked to the current merchant (related to either the OAuth token or API Key provided in the Authorisation header).

<ul id="profileTabs" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/webhooks-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/listWebhooksUsingGET','#profileTabs',timerRef); }, 500);
</script>
</div>
</div>


{% include links.html %}
