---
title: Webhooks for Credit Transfers
keywords: Webhooks Overview
summary: "Webhooks can be used to notify your internal systems when specific events occur in Nuapay."
sidebar: ct_sidebar
permalink: np_ctwhoverview.html
folder: prodNuapay
toc: false
---

{% include tip.html content="Webhooks are HTTP notifications, dispatched to a specified URL when certain events are triggered in Nuapay. Webhooks allow Nuapay to push updates or events to your system as soon as they occur rather than your systems needing to continually poll our system for changes." type="primary" %}

Webhooks processing can be summarised as follows:
* **Event Occurrence**: When an event happens in Nuapay (e.g., a payment is processed), a webhook is triggered.
* **HTTP Request**: Nuapay sends an HTTP POST request to your predefined URL (the webhook endpoint) of the receiving application.
* **Payload**: The request includes a payload of data (in JSON) related to the event.
* **Application Processes**: Your Receiving Application should process the incoming message and take specific actions based on the event.

<img src = 'images/wh-overview.png'>

You can use Webhooks for:

* **Real-time Notifications**: Nuapay can notify your app about the success or failure of a transaction.
* **Data Synchronization**: Webhooks help keep data synchronized across different systems. For instance, updates in a CRM system can be pushed automatically to an ERP system.
* **Automation**: Many workflows can be automated using webhooks, such as triggering processes (e.g., sending an email or updating records) when certain conditions are met.

For more information on the setup and configuration of Webhooks, see the general [Webhooks section](wh_overview.html) (under the **Get Started** menu).
