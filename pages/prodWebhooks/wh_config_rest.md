---
title: Webhooks Setup via RESTful API 
keywords: Webhooks Configuration
summary: "Details are provided in this section on setting up your Webhook Endpoint and listening for events via RESTful API"
sidebar: wh_sidebar
permalink: wh_config_rest.html
folder: prodWebhooks
toc: false
---

## Overview

{% include swagger_wh.html %}

Nuapay offers various RESTful Endpoints to allow you to manage your Webhooks. These APIs are available for use for individual merchants and for partners acting on behalf of their merchants. 

{% include note.html content="Partner users **must use APIs to set up, configure and manage Webhooks on behalf of their merchants**. " %}


Use these APIs to **create and manage** your Webhooks:

|Service|Method|Link|
|Create Webhook|POST|[Details](wh_restcreate.html)|
|Retrieve Webhook|GET|[Details](wh_restretrieve.html)|
|Update Webhook|PUT|[Details](wh_restupdel.html)|
|Delete Webhook|DELETE|[Details](wh_restupdel.html)|

Use these services to **Enable or Disable** your Webhooks:

|Service|Method|Link|
|Enable a Webhook|POST|[Details](wh_restenabdisab.html#enable-for-a-single-webhook)|
|Disable a Webhook|POST|[Details](wh_restenabdisab.html#disable-for-a-single-webhook)|
|Enable ALL Webhooks|POST|[Details](wh_restenabdisab.html#enable-all-webhooks)|
|Disable ALL Webhooks|POST|[Details](wh_restenabdisab.html#disable-all-webhooks)|

Use this to **list** the Webhooks currently configured:

|Service|Method|Link|
|List Webhooks|GET|[Details](wh_restlist.html)|


Before you can use Nuapay Webhooks you must set up a dedicated Endpoint on your infrastructure. See [Webhook Receiving Endpoint](wh_receivingep.html) for more on this.





{% include links.html %}
