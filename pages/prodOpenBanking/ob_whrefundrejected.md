---
title: Open Banking Payment Refunded Rejected Event
keywords: Payment Refunded Rejected Event Webhook 
summary: "Payment Refunded Rejected Webhook event"
sidebar: ob_sidebar
permalink: ob_whrefundrejected.html
folder: prodOpenBanking
toc: false
---
 
{% include webhook.html content="A refunded payment has been rejected; the PSU has not been credited funds. The associated refund object has a status of REFUND_REJECTED." %}


## Webhook Message Details

This Webhook has a single event type: <b>PaymentRefundRejected</b>

{% include tip.html content="For [Developer Dashboard](wh_config_ui.html#setting-up-a-webhook) users: select the **Open Banking Refund Rejected** event." %}


## Webhook Event Message Details

<p>
	The following table describes the details of the Webhook notification:</p>
<table cellspacing="0">
	
	<tbody>
		<tr>
			<th>Parent</th>
			<th>Parameter</th>
			<th>Type</th>
			<th>Mandatory/Optional</th>
			<th>Description</th>
		</tr>
		<tr>
			<td >root</td>
			<td>eventTimestamp</td>
			<td>number</td>
			<td>Mandatory</td>
			<td> The Unix epoch timestamp </td>
		</tr>
		<tr>
			<td>root</td>
			<td>eventType</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>PaymentRefundRejected</td>
		</tr>		
		<tr>
			<td>root</td>
			<td>resourceReference</td>
			<td>string</td>
			<td>optional</td>
			<td>This can be the business reference of the resource, useful when filtering events via the Webhooks area of the Developer Dashboard.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceReferenceType</td>
			<td>string</td>
			<td> optional</td>
			<td>This can be a business reference of the resource, useful when filtering events via the Webhooks area of the Developer Dashboard.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceUri</td>
			<td>string</td>
			<td>Mandatory</td>
			<td> This is URI of the refund resource. Use the URI in the <a href="ob_retrievepayment.html">Retrieve Payment</a> call.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceType</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is a refund resource.</td>
		</tr>
        <tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
			<td>Null </td>
		</tr>
        <tr>
			<td>root</td>
			<td>resourceOwner</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the identifier of the merchant resource to which this notification is linked.</td>
		</tr>
		
		
	</tbody>
</table>

## JSON Sample

The following is an example of a Refund Rejected event JSON:

<b>Headers</b>:


|POST| http://example.com/webhooks|
|Content-Type:| application/json;charset=UTF-8|
|[X-Signature](wh_receivingep.html#x-signature): |123ab01d030dee864fb44cc65a3be52ae591f46cde8d14d3e72fbc3790e4a304|
|Content-Length:| 261|
|X-Request-Id:| dc645679-71a5-498d-bb29-ec027948c7c1|

<b>JSON Request Body</b>
<pre>
<code class="json">{
    "eventTimestamp": 1501169079000,
    "eventType": "PaymentRefundRejected",   
    "resourceReference": "4892i45r76rg8b4d874r65",
    "resourceReferenceType": "reference",    
    "resourceUri": "/payments/t9rklm6lrp",
    "resourceType": "payment",
    "reasonCode": null,
    "resourceOwner": "tc47ygrg72"    
}</code>
</pre>



{% include links.html %}
