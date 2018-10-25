---
title: Webhooks Configuration
keywords: Webhooks Configuration
summary: "Details are provided in this section on setting up your Webhook Endpoint and listening for events"
sidebar: ob_sidebar
permalink: ob_whconfiguration.html
folder: prodOpenBanking
---

## Overview Setup

To set up Webhooks you will need to:

1. Create an endpoint.
1. Configure the Webhook(s) you require.
1. Listen for events.


Before you can use Nuapay Webhooks you must set up a dedicated Endpoint on your Web server. The steps required to configure your endpoint will vary depending on the Web server that you are currently using. Please consult with the documentation for your preferred Web server.

## Setting up a Webhook

<p>To set up a Webhook: </p>
  <ol>
    <li value="1">Log on to the Developer Dashboard (currently available from the Origix Corporate home page).</li>
    <li value="2">Click <b>Add Webhook</b>.</li>
    <li value="3">Add the required details in the pop-up dialog box:</li>
    <img src="/images/add_webhook.png" style="width: 390;height: 369;" />
    <li value="4">Specify: <ol><li value="1">The name of the Webhook notification. </li><li value="2">The URL of the Endpoint you configured.</li><li value="3">Status is set to Enabled by default (if Disabled no notifications are generated).</li><li value="4">Retry period (determines for how many days failed notifications will be retried. Retries are automatically generated every 30 minutes).</li><li value="5">Sign Key is the secret key that the application uses to sign the notification JSON&#160;body. The signature is sent in the request HTTP 'X-Signature' header. If you leave this field blank the application will automatically generate a key.</li><li value="6">The Event Types drop-down allows you to configure what events will trigger the notification to the Webhooks Endpoint URL. In the example above only Refunds will trigger a notification but you may define 1-n events as required.</li></ol></li>
    <li value="5">Click <b>Submit</b>.</li>
</ol>

## X-Signature

To ensure that you can be confident that the Webhook message received by your defined Endpoint has actually been dispatched from Nuapay, we encode the Sign Key (you configured in step 4 (e) above) using HMAC: Keyed-Hashing for Message Authentication .

Before transmitting the Webhook message to your Endpoint, Nuapay creates a hash value based on your Sign Key. Nuapay uses the Apache Commons HmacUtils codec for the encoding; the hashed value is then passed in the X-Signature.

````

import org.apache.commons.codec.digest.HmacUtils;
String xSignature = HmacUtils.hmacSha256Hex(signKey.getBytes(), body);

````


For more information on HMAC see <a href ="https://tools.ietf.org/html/rfc2104" target = "new">https://tools.ietf.org/html/rfc2104</a>

## Listening for Events

When an event occurs on your Nuapay account it is notified to your configured endpoint URL.

Notification Details - HTTP POST Request

|<b>Method</b>|<span class="label label-info">POST </span>|
|<b>Content-Type</b>|application/json|


<b>Extra Request Headers</b>

|**Header Name**|**Header Value**                                                                      |
|X-Request-Id   |UUID of the Webhook Notification                                                      |
|X-Signature    |Signature of the request JSON body, created with the Sign Key stored on the Webhook   |


<b>Request Body</b>

<table style="width: 100%;" class="Code">
	<col />
	<col style="width: 128px;" />
	<col />
	<tbody>
		<tr>
			<td style="font-weight: bold;">JSON Path</td>
			<td style="font-weight: bold;">Type</td>
			<td style="font-weight: bold;">Description</td>
		</tr>
		<tr>
			<td>eventTimestamp</td>
			<td>Number
						Max 19 chars
			</td>
			<td>The Epoch timestamp format of the date and time that the event was triggered</td>
		</tr>
		<tr>
			<td>eventType</td>
			<td>String
					Max 255 chars</td>
			<td>
				<p>The type of event to which this notification is related. The event can be one of the following, for example: </p>
				<ul>
					<li value="1">PaymentRecieved</li>
					<li value="2">PaymentReversed</li>
					
				</ul>
			</td>
		</tr>
		<tr>
			<td>resourceReference</td>
			<td>String
					Max 255 chars</td>
			<td>This is the reference to a specific resource (received or reversed payment). The type of reference is specified by the resourceReferenceType.</td>
		</tr>
		<tr>
			<td>resourceReferenceType</td>
			<td>String
					Max 255 chars</td>
			<td>This is the resource reference type to which the resourceReference is related.</td>
		</tr>
		<tr>
			<td>resourceUri</td>
			<td>String
					Max 255 chars</td>
			<td>
				<p>This is the URI to the resource being referenced in the event.
						You can use <a href="ob_retrievepayment.html">Retrieve Payment</a> to retrieve the payment details.</p>
				
			</td>
		</tr>
		<tr>
			<td>resourceType</td>
			<td>String
					Max 255 chars</td>
                    <td>The type of the resource to which the resourceUri is related; a <i>payment</i> resource in this scenario.</td>
		</tr>
		<tr>
			<td>reasonCode</td>
			<td>String
					Max 6 chars</td>
			<td>Null.</td>
		</tr>
	</tbody>
</table>

{% include links.html %}
