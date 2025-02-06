---
title: Credit Transfer Batch Failed Event
keywords: Credit Transfer Batch Failed Event Webhook
summary: "Credit Transfer Batch Failed Webhook event"
sidebar: ct_sidebar
permalink: np_whctcollfailed.html
folder: prodNuapay
toc: false
---

{% include webhook.html content="A CT Batch moves to FAILED status." %}

{% include wh-compatibility.html %}

## Failed vs Rejected Batch

It is important to distinguish between `FAILED` and `REJECTED` states, which both indicate unsuccessful processing but have different implications:

* A `FAILED` Batch occurs when the entire Batch fails validation checks before individual Credit Transfers (CTs) are created. This is a Batch-level failure triggered by a common error affecting the whole Batch. The Batch is marked as `FAILED`, and no CTs are created.
* `REJECTED` applies when individual CTs within a Batch fail specific validations during processing. This is a transaction-level failure, and a Batch can be marked as REJECTED even if only one CT fails. A REJECTED Batch can also have a mix of rejected and failed CTs.

The following table summarises the key differences:

| Feature           | FAILED                                           | REJECTED                                                       |
|-------------------|--------------------------------------------------|-----------------------------------------------------------------|
| **Scope**         | Batch-level                                 | Transaction-level (can include Batch-level failures)       |
| **Trigger**       | Failure of Batch-level validations          | Failure of individual CT validations during processing          |
| **CT Creation**   | No CTs are created                               | CTs are created, but some/all may fail or be rejected           |
| **Error Reporting** | `rejectDetails` on the Batch object      | `rejectDetails` on individual CT objects (and potentially the Batch) |
| **Example Reason** | Invalid originator account, incorrect total amount | Insufficient funds for a specific CT                           |


{% include tip.html content="**FAILED** signals an issue with the Batch data itself, preventing the creation of any CTs. **REJECTED** indicates that the Batch was initially valid, but individual CTs encountered issues during processing." %}


## Webhook Message Details

This Webhook has the following event type:

|**Webhook Event Type**| **Description**|
|CreditTransferBatchFailed|Triggered where a Credit Transfer Batch transitions to status = FAILED|

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
            <td>CreditTransferBatchFailed</td>
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
			<td>This is the type of the resource to which the URI is related. In this case it is a Credit Transfer Batch resource.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
            <td>The <a href="np_separeasons.html">SEPA Reason Code</a>, the <a href="np_bacsreasons.html"> Bacs Reason Code</a> (depending on the scheme) or the <a href="np_appreasons.html#ct-collection-application-error-codes"> Application Reason Code</a> (where a Batch has been rejected prior be being passed to Clearing).</td>
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
 "eventType": "CreditTransferBatchFailed",    
 "resourceReference": "E2E123456",
 "resourceReferenceType": "Reference",   
 "resourceUri": "/credittransfers/batches/rn4y5qgv2p",
 "resourceId": "rn4y5qgv2p",
 "resourceType": "CreditTransferBatch",
 "reasonCode": "CTC001",
 "resourceOwner": "878UJK",
 "resourceRemittanceInformation": null

}</code>
</pre>

{% include links.html %}
