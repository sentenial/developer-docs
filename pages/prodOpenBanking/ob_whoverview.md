---
title: Webhooks Overview 
keywords: Webhooks Overview
summary: "Webhooks can be used to notify your internal systems when specific Open Banking events occur."
sidebar: ob_sidebar
permalink: ob_whoverview.html
folder: prodOpenBanking
---


Webhooks are HTTP notifications, dispatched to a specified URL when certain Open Banking events are triggered. 

Webhooks may be managed: 

|Via the [Nuapay UI](ob_whconfiguration.html) using the Developer Dashboard - (for **merchant** users only)|
|Through [APIs](ob_whconfigurationrest.html) - (primarily for **partner** users)|


{% include note.html content="Webhooks configuration via API is also available to merchant users." %}


## Working With Webhook Notifications

When working with Webhooks note that:

* Webhook notifications are generated when specific events are triggered.
* Messages are dispatched individually (not batched) - once an event occurs the Webhook notification is generated and sent.
* A single payment can generate more than one Webhook message; for example when a payment is received and then later if it is reversed.
* All Webhook messages include a timestamp (Unix Epoch value), allowing you to determine if you receive a Webhook message out of sequence. For example it could be possible (although unlikely) that you receive a **payment reversed** notification BEFORE a **payment received** notification; the `eventTimestamp` allows you to correctly order notifications. 
(Note that The [Retrieve Payment](ob_retrievepayment.html) allows you to confirm the sataus of a payment at any given time).
* The Webhooks receiving endpoint should respond to Nuapay's incoming Webhook notifications to confirm receipt. The default is 10 seconds before timing out.
* Notifications may be configured with a retry mechanism. The retry period, configured in days, determines for how long failed notifications will be retried. Retries are automatically generated every 30 minutes. Once the configured time has been reached no new attempts will be made to deliver the message. You may still determine a payment status at any point using [Retrieve Payment](ob_retrievepayment.html)





