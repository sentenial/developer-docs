---
title: Create Webhook
keywords: Create Open Banking Webhook
summary: "Create Open Banking Webhook"
sidebar: ob_sidebar
permalink: ob_whrestcreate.html
folder: prodOpenBanking
toc: false
---

## API Details 

The Create Webhook service generates a Webhook that will be passed to your defined Endpoint when a certain event occurs, for example when an Open Banking payment is received on your Nuapay account.

If required, you can configure a single Webhook destination to respond to one or many event types. 

Use the `retryNumberOfDays` to handle Webhook message failures by defining for how long Nuapay should attempt to retry sending the Webhook notification; retries are made every 30 minutes so if you set the value here as = 1 then retries will be made every 30 minutes for 24 hours (or until a retry is successful).

{% include swagger_wh.html %}

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/webhooks-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/createWebhookUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
