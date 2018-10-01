---
title: Accepted Direct Debit Event
keywords: Accepted Direct Debit Event Webhook 
summary: "Accepted Direct Debit Webhook event"
sidebar: np_sidebar
permalink: np_whaccepteddd.html
folder: prodNuapay
toc: false
---
 
{% include webhook.html content="A Direct Debit payment's status moves to ACCEPTED (on its value date)" %}


## Webhook Message Details

This Webhook has a single event type: <b>DirectDebitAccept</b>


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
			<td>DirectDebitAccept</td>
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
			<td> This is URI of the Direct Debit resource. Use the URI in the <a href="np_retrievedirectdebit.html">Retrieve Direct Debit</a> call.</td>
		</tr>
		<tr>
			<td>resourceDetails</td>
			<td>type</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is a Direct Debit resource.</td>
		</tr>
		<tr>
			<td>resourceDetails</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
			<td>Null for Direct Debits in ACCEPTED status. </td>
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

The following is an example of a Direct Debit Reject event JSON:

```js
POST http://example.com/webhooks
Content-Type: application/json;charset=UTF-8
X-Signature: 521ab01d030dee864fb44cc65a3be52ae591f46cde8d14d3e72fbc3790e4a304
Content-Length: 261
X-Request-Id: dc645679-71a5-498d-bb29-ec027948c7c1
	{
		"eventTimestamp": 1501169079000,
		"eventType": "DirectDebitAccept",
		"resourceReference": "Webhook1",
		"resourceReferenceType": "EndToEndId",
		"resourceUri": "/schemes/p2lqa394mv/mandates/lbyjxj5ebd/directdebits/wew3qnvdmq",
		"resourceType": "DirectDebit",
		"reasonCode": null
	}
````


{% include links.html %}
