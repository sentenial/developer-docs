---
title: Credit Transfer Batch Complete With Errors Event
keywords: Credit Transfer Batch Complete With Errors Event Webhook
summary: "Credit Transfer Batch Complete With Errors Webhook event"
sidebar: ct_sidebar
permalink: np_whctcollcompleteerror.html
folder: prodNuapay
toc: false
---

{% include webhook.html content="A CT Batch moves to COMPLETE status." %}

{% include wh-compatibility.html %}

## Webhook Message Details

This Webhook has the following event type:

|**Webhook Event Type**| **Description**|
|CreditTransferBatchCompleteWithErrors|Triggered where a Credit Transfer Batch transitions to status = COMPLETE WITH ERRORS|

## Webhook Event Message Details

<p>The following table describes the details of the Webhook notification:</p>

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
            <td>CreditTransferBatchCompleteWithErrors</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceReference</td>
			<td>string</td>
			<td>optional</td>
			<td>This can be the business reference of the resource, useful when filtering events via the Webhooks area of the Nuapay Console.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceReferenceType</td>
			<td>string</td>
			<td> optional</td>
			<td>This can be a business reference of the resource, useful when filtering events via the Webhooks area of the Nuapay Console.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceUri</td>
			<td>string</td>
			<td>Mandatory</td>
			<td> This is the URI of the resource. Use the URI to retrieve more details - see <a href ="np_ctviewcoll.html">Retrieve Credit Transfer Batch</a>.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceType</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is a Credit Transfer Batch resource.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>Optional</td>
			<td>Null</td>
		</tr>
        <tr>
			<td>root</td>
			<td>resourceOwner</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the identifier of the merchant resource to which this notification is linked.</td>
		</tr>
		<tr>
	<td>root</td>
	<td>resourceRemittanceInformation</td>
	<td>string</td>
	<td>optional</td>
	<td>Null.</td>
</tr>


	</tbody>
</table>

## JSON Sample

The following is an example of a Credit Transfer Batch Rejection event JSON:

<b>Headers</b>:


|POST| http://example.com/webhooks|
|Content-Type:| application/json;charset=UTF-8|
|x-signature: |123ab01d030dee864fb44cc65a3be52ae591f46cde8d14d3e72fbc3790e4a304|
|Content-Length:| 261|
|X-Request-Id:| dc645679-71a5-498d-bb29-ec027948c7c1|

<b>JSON Request Body</b>
<pre>
<code class="json">{

 "eventTimestamp": 1501169079000,
 "eventType": "CreditTransferBatchCompleteWithErrors",    
 "resourceReference": "E2E123456",
 "resourceReferenceType": "Reference",   
 "resourceUri": "/credittransfers/batches/w24y5qgv2p",
 "resourceType": "CreditTransferBatch",
 "reasonCode": null,
 "resourceOwner": "878UJK",
 "resourceRemittanceInformation": null

}</code>
</pre>

{% include links.html %}
