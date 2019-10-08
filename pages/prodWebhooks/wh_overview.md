---
title: Webhooks Overview 
keywords: Webhooks Overview
summary: "Webhooks can be used to notify your internal systems when specific events occur."
sidebar: wh_sidebar
permalink: wh_overview.html
folder: prodWebhooks
---


Webhooks are HTTP notifications, dispatched to a specified URL when certain events are triggered. 

Webhooks may be managed: 

|Via the [User Interface](wh_config_ui.html) using the Nuapay Developer Dashboard - (for **merchant** users only)|
|Through [APIs](wh_config_rest.html) - (primarily for **partner** users)|


{% include note.html content="Webhooks configuration via API is also available to merchant users." %}


## Working With Webhook Notifications

When working with Webhooks note that:

* Webhook notifications are generated when specific events are triggered.
* Messages are dispatched individually (not batched) - once an event occurs the Webhook notification is generated and sent.
* A single payment can generate more than one Webhook message; for example when an Open Banking payment is received and then later if it is reversed (or where a Direct Debit payment is Accepted and then later Returned unpaid).
* All Webhook messages include a timestamp (Unix Epoch value), allowing you to determine if you receive a Webhook message out of sequence. For example it could be possible (although unlikely) that you receive an Open Banking **payment reversed** notification BEFORE a **payment received** notification; the `eventTimestamp` allows you to correctly order notifications. 
* The Webhooks receiving endpoint should respond to the incoming Webhook notifications to confirm receipt. The default is 10 seconds before timing out.
* Notifications may be configured with a retry mechanism. The retry period, configured in days, determines for how long failed notifications will be retried. Retries are automatically generated every 30 minutes. Once the configured time has been reached no new attempts will be made to deliver the message.





