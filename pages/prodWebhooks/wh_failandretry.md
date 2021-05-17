---
title: Webhook Failure and Retry Support
keywords: Webhooks Failure and Retry Support
summary: "Details on Webhook notification failure, retry, batching and sequencing "
sidebar: wh_sidebar
permalink: wh_failandretry.html
folder: prodWebhooks
---


## Failed Webhook Notification and Retry Mechanism
When a Webhook notification is dispatched, the system expects the receiving endpoint to acknowledge receipt with an HTTP success status (200)

Note that:
* The Webhook module will timeout after **10 seconds** if the receiving endpoint has not acknowledged the receipt of the notification.
* Failed notifications are retried based on the Retry strategy defined in the configuration of the webhook. 
* You can configure your Webhook notifications to retry for a period of time e.g. for 1 day (this can be specified in the `retryNumberOfDays` - see [Create Webhook](wh_restcreate.html) or via the [UI](wh_config_ui.html#setting-up-a-webhook)). 
* Notifications that fail to be delivered will be retried *every 30 minutes* until successful or until the configured retry period is reached. After a final unsuccessful retry, the webhook notification is marked as Failed.
* A `GET` request can also be used to retrieve the details of any given resource, where a Webhook notification has failed. If you require the specific Webhook to be reissued after the retry period has elapsed, please contact the Support team.

## Webhook Batching and Sequencing 

Webhooks notifications are never batched: notifications are dispatched individually. 

Note too that, while unlikely, it is possible to receive notifications out of sequence. Every notification includes an `eventTimestamp` (a Unix Epoch value), which will allow you to determine the correct ordering of notifications. This could be useful, for example, if you were to receive a Direct Debit `RETURN` notification **prior** to an `ACCEPT` notification, for the same transaction. Because the events that trigger the Webhook notifications would be an ACCEPT event initally and then a RETURN at some point after that, the Epoch values provided in the notifications allow you to put the notifications in the correct sequence (the RETURN having the more recent Epoch value). 


{% include links.html %}







