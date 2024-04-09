---
title: File Status Update Event
keywords: File Status Update Event
summary: "File status change event"
sidebar: fm_sidebar
permalink: fm_whfile_status.html
folder: prodFileMgmt
---

{% include webhook.html content="A file transitions from one processing status to another." %}

{% include wh-compatibility.html %}

## Webhook Message Details

This Webhook notifies you of any file status changes.

The following event type is possible:

|**Webhook Event Type**| **Description**|
|FileStatusUpdated|A file is initially QUEUED (awaiting processing) and may transition from intermediary statuses to a final status. You may configure Webhook notifications as required, to be notified when files transition to specific statuses.|

## File statuses

{% include tip.html content="Files are referred to as `Import` when they are initially passed to Nuapay and validations are carried out. Successfully processed Import files (COMPLETE or COMPLETE WITH ERROR) are then mapped to an `Export` file. This is the file that is passed to Clearing for processing, where the actual settlement of funds occurs. Export files may transition to ACCEPTED or PARTIALLY_ACCEPTED." %}

It is possible to receive a Webhook notification for files that transition to any of the following statuses:

|Status|Description|
|------|-----------|
|PENDING|The collection date is in the future and the file has not yet been selected for processing.|
|PENDING SETTLEMENT|The export file has been passed to Clearing but an acknowledgement has not yet been received.|
|ACCEPTED|An export file has been passed to Clearing and an Acknowledgement (ACK) has been received.|
|PARTIALLY_ACCEPTED|An export file has been passed to Clearing and a partial Acknowledgement (ACK) has been received.|
|COMPLETE|All transactions in the Import file have been successfully processed.|
|COMPLETE_WITH_ERRORS|Some but not all transactions in the import file have been successfully processed.|
|REJECTED|There were errors in the import file and it has not been possible to process it.|

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
			<td>Always set to FileStatusUpdated. </td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceTechnicalId</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>The unique identifier of the file (the internal Database ID). </td>
		</tr>			
		<tr>
			<td>root</td>
			<td>resourceReference</td>
			<td>string</td>
			<td>optional</td>
			<td>The business reference of the resource: Message ID.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceReferenceType</td>
			<td>string</td>
			<td> optional</td>
			<td>The business reference of the resource: the actual Message ID.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceUri</td>
			<td> string</td>
			<td>Mandatory</td>
			<td>The URI of the file resource.  </td>
		</tr>		
		<tr>
			<td>root</td>
			<td>resourceType</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is a File resource.</td>
		</tr>   
    <tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
            <td> Always null for files.</td>
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
<td>Always null for files.</td>
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
  "eventType": "FileStatusUpdated",
      "resourceTechnicalId": 500001,
      "resourceReference": "202310171191612G08-05",
      "resourceReferenceType": "MessageId",
      "resourceUri": "/files/j29pwvl5bx",
      "resourceType": "File",
      "reasonCode": null,
      "resourceOwner": "tc47ygrg72",
      "resourceRemittanceInformation": null      
}</code>
</pre>

{% include links.html %}
