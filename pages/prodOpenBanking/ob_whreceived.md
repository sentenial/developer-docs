---
title: Payment Received Event
keywords: Received Payment Event Webhook 
summary: "Received Payment Webhook event"
sidebar: ob_sidebar
permalink: ob_whreceived.html
folder: prodNuapay
toc: false
---
 
{% include webhook.html content="An Open Banking payment is credited to the merchant's Nuapay account." %}


## Webhook Message Details

This Webhook has a single event type: <b>PaymentRecieved</b>


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
			<td>PaymentRecieved</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceTechnicalId</td>
			<td>number</td>
			<td>Mandatory</td>
            <td>Unique identifier</td>
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
			<td>resourceDetails</td>
			<td> object</td>
			<td>Mandatory</td>
			<td>Resource specific data grouping object </td>
		</tr>
		<tr>
			<td>resourceDetails</td>
			<td>uri</td>
			<td>string</td>
			<td>Mandatory</td>
			<td> This is URI of the payment resource. Use the URI in the <a href="ob_retrievepayment.html">Retrieve Payment</a> call.</td>
		</tr>
		<tr>
			<td>resourceDetails</td>
			<td>type</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is a payment resource.</td>
		</tr>
		<tr>
			<td>resourceDetails</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
			<td>Null </td>
		</tr>
		<tr>
			<td>root</td>
			<td>organizationId</td>
			<td>number</td>
			<td>Mandatory</td>
			<td> The unique merchant identifier </td>
		</tr>
	</tbody>
</table>

## JSON Sample

The following is an example of a Received Payment event JSON:

<b>Headers</b>:


|POST| http://example.com/webhooks|
|Content-Type:| application/json;charset=UTF-8|
|X-Signature: |123ab01d030dee864fb44cc65a3be52ae591f46cde8d14d3e72fbc3790e4a304|
|Content-Length:| 261|
|X-Request-Id:| dc645679-71a5-498d-bb29-ec027948c7c1|

<b>JSON Request Body</b>
<pre>
<code class="json">{
  "eventTimestamp": 1501169079000,
  "eventType": "PaymentRecieved",
  "resourceTechnicalId": 500006,
  "resourceReference": "reference",
  "resourceReferenceType": "reference",
  "resourceDetails": {		
    "uri": "/payments/n7rklmvdmq",
    "type": "payment",
    "reasonCode": null
  },
  "organizationId":1000
}</code>
</pre>



{% include links.html %}
