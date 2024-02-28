---
title: Webhooks Setup via the User Interface
keywords: Webhooks Configuration
summary: "Details are provided in this section on setting up your Webhook Endpoint and listening for events via the Nuapay User Interface"
sidebar: wh_sidebar
permalink: wh_config_ui.html
folder: prodWebhooks
---

## Overview Setup

To set up Webhooks you will need to:

1. Create an endpoint.
1. Configure the Webhook(s) you require.
1. Listen for events (see the [Receiving Endpoint](wh_receivingep.html) section for more on this).


Note that before you can use Webhooks you must set up a dedicated Endpoint on your infrastructure. (See [Webhook Receiving Endpoint](wh_receivingep.html) for more on this).

## Setting up a Webhook

<p>To set up a Webhook you must have <a href = "prod_consoleoverview.html"> Nuapay Console / Developer Dashboard</a> access: </p>
  <ol>
    <li value="1">Log on to the Nuapay Console. </li>  
    <li value="2">Click <b>Webhoks</b> from the left-hand menu and click <strong>Add Webhook</strong>.</li>
    <li value="3">Add the required details in the pop-up dialog box:</li>
    <img src="images/add_webhook_ob.png" />
    <li value="4">Specify: <ol><li value="1">The name of the Webhook notification. </li><li value="2">The URL of the Endpoint you configured.</li><li value="3">Status is set to Enabled by default (if Disabled no notifications are generated).</li><li value="4">Retry period (determines for how many days failed notifications will be retried. Retries are automatically generated every 30 minutes). In the screen above the setting is 1 day so retries will be made every 30 minutes for 24 hours (or until a retry is successful).</li><li value="5">Sign Key is the secret key that the application uses to sign the notification JSON&#160;body. The signature is sent in the request HTTP 'x-signature' header. If you leave this field blank the application will automatically generate a key.</li><li value="6">The Event Types drop-down allows you to configure what events will trigger the notification to the Webhooks Endpoint URL. In the example above only <b>Payment Received</b> will trigger a notification but you may define 1-n events as required.</li></ol></li>
    <li value="5">Click <b>Submit</b>.</li>
</ol>

Once you have set up the Webhook, you will need to configure a [Receiving Endpoint](wh_receivingep.html).

{% include links.html %}
