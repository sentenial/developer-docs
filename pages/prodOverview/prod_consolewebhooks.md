---
title: Nuapay Console Webhook Configuration
keywords: Nuapay Webhook Configuration
summary: "Manage Webhooks via the Console."
sidebar: productOverview_sidebar
permalink: prod_consolewebhooks.html
folder: prodOverview
---
## Webhook Configuration
{% include note.html content="The following screens relate to a merchant but the steps are identical for partner users." %}

To access the Webhook configuration:

1. Click **Webhooks** from the left-side menu.
1. Or view the **Recent Webhooks** area of the dashboard.

To add a new Webhooks:

1. Click **Add Webhook**.
1. Specify:
   * The `Name` of the Webhook notification.
   * The `Webhook Endpoint URL` of the Endpoint you configured.
   * The Webhook `Status` is set to Enabled by default (if set to Disabled then no notifications are generated).
   * The `Retry Failed Events` period (determines for how many days failed notifications will be retried. Retries are automatically generated every 30 minutes). In the screen below the setting is `1 day` so retries will be made every 30 minutes for 24 hours (or until a retry is successful).
   * `Sign Key` is the secret key that the application uses to sign the notification JSON&#160;body. The signature is sent in the request HTTP 'x-signature' header. If you leave this field blank the application will automatically generate a key.
   * The `Event Types` drop-down allows you to configure what event(s) will trigger the notification to the Webhooks Endpoint URL. You may define 1-n events as required.
<img src = "images/console_webhooks.png">
1. Click **Submit**.

{% include tip.html content="Webhooks configured at the Partner level will be triggered for all Merchants configured under that Partner." %}


{% include links.html %}
