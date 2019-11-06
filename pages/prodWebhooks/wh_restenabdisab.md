---
title: Enable/Disable Webhook
keywords: Enable/Disable Open Banking Webhook
summary: "Enable/Disable Open Banking Webhook"
sidebar: wh_sidebar
permalink: wh_restenabdisab.html
folder: prodOpenBanking
toc: true
---

## API Details 

{% include swagger_wh.html %}

{% include urls.html %}

It is possible to enable or disable a single Webhook, when you provide its Webhook identifier. 
Alternaltively you can use the `enable all` or `disable all` services to carry out the required action on ALL configured Webhooks for the given merchant.

|<span class="label label-info">Post</span>|Enable Webhook|
|<span class="label label-info">Post</span>|Disable Webhook|
|<span class="label label-info">Post</span>|Enable All|
|<span class="label label-info">Post</span>|Disable All|




{% include note.html content="Webhooks when first created are  enabled by default." %}

## Enable for a Single Webhook

<ul id="profileTabs" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/webhooks-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/enableWebhookUsingPOST','#profileTabs',timerRef); }, 500);
</script>
</div>
</div>

## Disable for a Single Webhook

<ul id="profileTabs2" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef2 = setInterval(function() { getDocs('operation/disableWebhookUsingPOST','#profileTabs2',timerRef2); }, 500);
</script>
</div>
</div>

## Enable ALL Webhooks

<ul id="profileTabs3" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef3 = setInterval(function() { getDocs('operation/enableAllWebhooksUsingPOST','#profileTabs3',timerRef3); }, 500);
</script>
</div>
</div>

## Disable ALL Webhooks

<ul id="profileTabs4" class="nav nav-tabs">
</ul>
  
{% include redoc.html %}
   
var timerRef4 = setInterval(function() { getDocs('operation/disableAllWebhooksUsingPOST','#profileTabs4',timerRef4); }, 500);
</script>
</div>
</div>

{% include links.html %}
