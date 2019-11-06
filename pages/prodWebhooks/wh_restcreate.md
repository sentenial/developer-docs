---
title: Create Webhook
keywords: Create Webhook
summary: "Create Webhook"
sidebar: wh_sidebar
permalink: wh_restcreate.html
folder: prodWebhooks
toc: false
---

## API Details 

The Create Webhook service generates a Webhook that will be passed to your defined Endpoint when a certain event occurs, for example when an Open Banking payment is received on your Nuapay account.

If required, you can configure a single Webhook destination to respond to one or many event types. 

Use the `retryNumberOfDays` to handle Webhook message failures by defining for how long Nuapay should attempt to retry sending the Webhook notification; retries are made every 30 minutes so if you set the value here as = 1 then retries will be made every 30 minutes for 24 hours (or until a retry is successful).

{% include swagger_wh.html %}


{% include urls.html %}


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
