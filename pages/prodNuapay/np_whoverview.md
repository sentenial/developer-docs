---
title: Webhooks Overview
keywords: Webhooks Overview
summary: "Webhooks can be used to notify your internal systems when specific events occur in Nuapay."
sidebar: np_sidebar
permalink: np_whoverview.html
folder: prodNuapay
toc: false
---


Webhooks are HTTP notifications, dispatched to a specified URL when certain events are triggered in Nuapay. When working with the Nuapay API you will generate a request and receive a response; when using Webhooks you will receive a notification (similar to an API response) when certain activities (events) occur on your Nuapay account.

## Working With Webhook Notifications

When working with Webhooks note that:

* Webhook notifications are generated when specific events are triggered.
* Messages are dispatched individually (not batched) - once an event occurs the Webhook notification is generated and sent.
* A single payment can generate more than one Webhook message; for example when a payment is accepted and then later if it is returned.
* All Webhook messages include a timestamp (Unix Epoch value), allowing you to determine if you receive a Webhook message out of sequence. For example it could be possible (although unlikely) that you receive a **Return** notification BEFORE an **Accept** notification; the `eventTimestamp` allows you to correctly order notifications. 
(Note that The [Retrieve Direct Debit](np_retrievedirectdebit.html) service allows you to confirm the sataus of a Direct Debit payment at any given time).
* The Webhooks receiving endpoint should respond to Nuapay's incoming Webhook notifications to confirm receipt. The default is 10 seconds before timing out.
* Notifications may be configured with a retry mechanism. The retry period, configured in days, determines for how long failed notifications will be retried. Retries are automatically generated every 30 minutes. Once the configured time has been reached no new attempts will be made to deliver the message. You may still determine a payment status at any point using [Retrieve Direct Debit](np_retrievedirectdebit.html).