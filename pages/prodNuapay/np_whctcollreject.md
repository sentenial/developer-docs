---
title: Credit Transfer Batch Reject Event
keywords: Credit Transfer Batch Reject Event Webhook
summary: "Credit Transfer Batch Reject Webhook event"
sidebar: ct_sidebar
permalink: np_whctcollreject.html
folder: prodNuapay
toc: false
---

{% include webhook.html content="A CT Batch moves to REJECTED status." %}

{% include wh-compatibility.html %}

## Failed vs Rejected Batches

It is important to distinguish between `FAILED` and `REJECTED` states, which both indicate unsuccessful processing but have different implications:

* A `FAILED` batch occurs when the entire batch fails validation checks before individual Credit Transfers (CTs) are created. This is a batch-level failure triggered by a common error affecting the whole batch. The batch is marked as `FAILED`, and no CTs are created.
* `REJECTED` applies when individual CTs within a batch fail specific validations during processing. This is a transaction-level failure, and a batch can be marked as REJECTED even if only one CT fails. A REJECTED batch can also have a mix of rejected and failed CTs.

The following table summarises the key differences:

| Feature           | FAILED                                           | REJECTED                                                       |
|-------------------|--------------------------------------------------|-----------------------------------------------------------------|
| **Scope**         | Batch-level                                 | Transaction-level (can include batch-level failures)       |
| **Trigger**       | Failure of batch-level validations          | Failure of individual CT validations during processing          |
| **CT Creation**   | No CTs are created                               | CTs are created, but some/all may fail or be rejected           |
| **Error Reporting** | `rejectDetails` on the batch object      | `rejectDetails` on individual CT objects (and potentially the batch) |
| **Example Reason** | Invalid originator account, incorrect total amount | Insufficient funds for a specific CT                           |


{% include tip.html content="**FAILED** signals an issue with the batch data itself, preventing the creation of any CTs. **REJECTED** indicates that the batch was initially valid, but individual CTs encountered issues during processing." %}

## Webhook Message Details

This Webhook has the following event types:

|**Webhook Event Type**| **Description**|
|CreditTransferBatchRejected|Triggered where a Credit Transfer batch transitions to status = REJECTED|

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
            <td>CreditTransferBatchRejected</td>
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
			<td>This can be a business reference of the resource, useful when filtering events via the Webhooks area of the Developer Dashboard.</td>
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
			<td>optional</td>
            <td>The <a href="np_separeasons.html">SEPA Reason Code</a>, the <a href="np_bacsreasons.html"> Bacs Reason Code</a> (depending on the scheme) or the <a href="np_appreasons.html#ct-collection-application-error-codes"> Application Reason Code</a> (where a batch has been rejected prior be being passed to Clearing).</td>
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
 "eventType": "CreditTransferBatchRejected",    
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
