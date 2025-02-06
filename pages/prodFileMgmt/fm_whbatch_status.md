---
title: Batch Status Update Event
keywords: Batch Status Update Event
summary: "Batch status change event"
sidebar: fm_sidebar
permalink: fm_whbatch_status.html
folder: prodFileMgmt
---

{% include webhook.html content="A batch transitions from one status to another." %}

{% include wh-compatibility.html %}

## Webhook Message Details

This Webhook notifies you of any batch status changes.

The following event type is possible:

|**Webhook Event Type**| **Description**|
|BatchStatusUpdated|A batch (a collection of transactions within a file) may transition to various statuses. You may configure Webhook notifications as required, to be notified when these transitions occur.|

## Batch statuses

It is possible to receive a Webhook notification for any of the following status changes:

|Status|Description|
|------|-----------|
|COMPLETE|The batch (and all transactions within it) in the Import file have been successfully processed.|
|COMPLETE_WITH_ERRORS|Some but not all transactions in the batch have been successfully processed.|
|PENDING|The collection date is in the future and the batch has not yet been selected for processing.|
|PENDING SETTLEMENT|The batch has been picked up for processing but has not transitioned to a final status.|
|REJECTED|There were errors in the import batch and it has not been possible to process it.|
|REVOKED|The import batch has been cancelled. The transactions in the batch will not be processed: the batch will not be passed to Clearing in an Export file. See [Revoke Direct Debit](np_revokedirectdebit.html) for more on this.|
|SETTLED|The batch has be exported and settled.|
|RECALLED|An export file has been passed to Clearing but has been cancelled prior to settlement.|

{% include note.html content="It is not always possible to recall batches. In order to do this you will need to contact Nuapay Support as early as possible after your file has been exported and they will attempt to initiate the recall process." %}





You may configure your notifications to be triggered for any of these statuses or for all. Configure your Webhooks as required via the [Nuapay Console](prod_consolewebhooks.html).

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
			<td>Always set to BatchStatusUpdated. </td>
		</tr>		
		<tr>
			<td>root</td>
			<td>resourceReference</td>
			<td>string</td>
			<td>optional</td>
			<td>The business reference of the resource: the Batch Reference.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceReferenceType</td>
			<td>string</td>
			<td> optional</td>
			<td>The business reference of the resource: the BatchReference.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceUri</td>
			<td> string</td>
			<td>Mandatory</td>
			<td>The URI of the batch resource.  </td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceId</td>
			<td> string</td>
			<td>Mandatory</td>
			<td>The encoded technical ID of the resource being referenced in the event. </td>
		</tr>		
		<tr>
			<td>root</td>
			<td>resourceType</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is a batch resource.</td>
		</tr>   
    <tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
            <td> Always null for batches.</td>
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
<td>Always null for batches.</td>
</tr>
	</tbody>
</table>

## JSON Sample

The following is an example of a File Status Update event JSON:

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
  "eventType": "BatchStatusUpdated",
	"resourceReference": "CRCUR09052023IE98ULSB98644073416",
	"resourceReferenceType": "BatchReference",  
	"resourceUri": "/files/j29pwvl5bx/batches/w24y5qgv2p",
	"resourceId": "w24y5qgv2p",
	"resourceType": "Batch",
	"reasonCode": null,
	"resourceOwner": "tc47ygrg72",
	"resourceRemittanceInformation": null
}</code>
</pre>

{% include links.html %}
