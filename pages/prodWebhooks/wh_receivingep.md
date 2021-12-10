---
title: Receiving Endpoint
keywords: Webhooks Receiving Endpoint
summary: "Webhook notifications are passed to your configured Endpoint; this section gives you some important security and configuration information to consider when setting up your receiving endpoint."
sidebar: wh_sidebar
permalink: wh_receivingep.html
folder: prodWebhooks
---


{% include note.html content="The configuration of your (receiving) Endpoint will be specific to your chosen Web server and architecture and is out of scope for this documentation. Here we assume that you have configured the Endpoint that you will be using for processing all Webhook notifications transferred to the Endpoint from Nuapay." %}

## X-Signature
To ensure that you can be confident that the Webhook message received by your defined Endpoint has actually been dispatched from Nuapay, we encode the Sign Key (as configured on the Add Webhook pop-up via the [Developer Dashboard screen](ob_whconfiguration.html) or via the `signKey` value in the [Create Webhook](ob_whrestcreate.html) API) using HMAC: Keyed-Hashing for Message Authentication .

Before transmitting the Webhook message to your Endpoint, Nuapay creates a hash value based on your Sign Key. Nuapay uses the Apache Commons HmacUtils codec for the encoding; the hashed value is then passed in the X-Signature.

````

import org.apache.commons.codec.digest.HmacUtils;
String xSignature = HmacUtils.hmacSha256Hex(signKey.getBytes(), body);

````


For more information on HMAC see <a href ="https://tools.ietf.org/html/rfc2104" target = "new">https://tools.ietf.org/html/rfc2104</a>

## Listening for Events

When an event occurs it is notified to your configured endpoint URL.

Notification Details - HTTP POST Request

|<b>Method</b>|<span class="label label-info">POST </span>|
|<b>Content-Type</b>|application/json|


<b>Extra Request Headers</b>

|**Header Name**|**Header Value**                                                                      |
|X-Request-Id   |UUID of the Webhook Notification                                                      |
|X-Signature    |Signature of the request JSON body, created with the Sign Key stored on the Webhook   |


<b>JSON Body</b>

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
				<p>The type of event to which the notification is related. </p>				
			</td>
		</tr>
		<tr>
			<td>resourceReference</td>
			<td>String
					Max 255 chars</td>
			<td>This is the reference to a specific resource e.g. an End-to-End Identifier for a Direct Debit transaction. The type of reference is specified by the resourceReferenceType.</td>
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
				<p>This is the URI to the resource being referenced in the event.</p>
			</td>
		</tr>
		<tr>
			<td>resourceType</td>
			<td>String
					Max 255 chars</td>
                    <td>The type of the resource to which the resourceUri is related.</td>
		</tr>
		<tr>
			<td>resourceOwner</td>
			<td>String
					Max 255 chars</td>
                    <td>This is the identifier of the merchant resource to which the notification is linked.</td>
		</tr>
		<tr>
			<td>resourceRemittanceInformation</td>
			<td>String
					Max 140 chars</td>
										<td>Remittance Information specific to the transaction.</td>
		</tr>
		<tr>
			<td>reasonCode</td>
			<td>String
					Max 6 chars</td>
			<td>The reason code, where applicable (e.g. where the Webhook relates to a rejected Direct Debit payment).</td>
		</tr>
	</tbody>
</table>

{% include tip.html content="Nuapay may update Webhooks from time to time and it is important to consider our [Versioning and Backward Compatibility](prod_versioning.html) guidelines when developing your solution. We recommend that the code that you write today is designed to be robust enough to handle any future changes (where a new Webhook parameter is added to (or removed from) a specific Webhook, for example). " %}


For details of the Webhook Event messages and `JSON` samples, see the events descriptions provided under your required Product (i.e. [Direct Debits & Credit Transfers](np_whoverview.html), [Electronic Mandates](em_whoverview.html), [Open Banking](ob_whoverview.html), etc.)


## Webhook-Triggering IPs

Nuapay Webhooks are triggered from the following IP addresses:

|**Production**:|217.114.175.30|
|**Sandbox**:| 149.5.33.51, 149.5.33.52, 149.5.33.53, 87.252.222.190|


{% include note.html content="Nuapay may update these IP addresses periodically. Merchants/Partners will be given advanced notice of any changes (at least 30 days' notice will be provided)." %}


{% include links.html %}
