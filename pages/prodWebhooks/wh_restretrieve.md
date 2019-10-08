---
title: Retrieve Webhook
keywords: Retrieve Webhook
summary: "Retrieve Webhook"
sidebar: wh_sidebar
permalink: wh_restretrieve.html
folder: prodWebhooks
toc: false
---

## API Details 

The Retrieve Webhook service allows you to pass a Webhook Identifier in your request to return details of a previously configured Webhook.

{% include swagger_wh.html %}

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/webhooks-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getWebhookUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
