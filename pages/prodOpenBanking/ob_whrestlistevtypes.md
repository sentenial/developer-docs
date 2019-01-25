---
title: List Event Types
keywords: List Event Types
summary: "List all event types related to the given merchant"
sidebar: ob_sidebar
permalink: ob_whrestlistevtypes.html
folder: prodOpenBanking
toc: false
---

## API Details 

The List Event Types service will return an array of configured Event Type linked to the current merchant (related to either the OAuth token or API Key provided in the Authorisation header).

<ul id="profileTabs" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/webhooks-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getEventTypesUsingGET','#profileTabs',timerRef); }, 500);
</script>
</div>
</div>


{% include links.html %}
