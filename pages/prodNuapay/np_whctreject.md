---
title: Credit Transfer Reject Event
keywords: Credit Transfer Reject Event Webhook
summary: "Credit Transfer Reject Webhook event"
sidebar: np_sidebar
permalink: np_whctreject.html
folder: prodNuapay
toc: false
---

{% include webhook.html content="A PAIN.002 Import with a Credit Transfer rejection OR a Credit Transfer payment initially created with a future execution date is rejected for insufficient funds when processed on that future execution date (the payment is rejected with a Nuapay CT042 - 'Insufficient funds' error code)." %}

{% include wh-compatibility.html %}

## Webhook Message Details

This Webhook has the following event types:

|**Webhook Event Type**| **Description**|
|CreditTransferReject|Triggered where a PAIN.002 import updates a Credit Transfer transaction to status = REJECTED|
|CreditTransferCancel|Triggered where a PAIN.002 import updates a Credit Transfer transaction to status = CANCELLED. A Credit Transfer is updated to CANCELLED where the [SEPA Reason Code](np_separeasons.html) is one of the following: CUST, CUTA, DUPL, UPAY|

{% include tip.html content="Where a future-dated Credit Transfer is rejected for insufficient funds, an internal Nuapay error (CT042) is applied. This is an internal reject i.e. the transaction is rejected prior to being passed to Clearing."%}

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
            <td>Either <b>CreditTransferReject </b> <br/> or <br/> <b>CreditTransferCancel</b></td>
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
			<td>resourceUri</td>
			<td>string</td>
			<td>Mandatory</td>
			<td> This is the URI of the resource. Use the URI to retrieve more details - see <a href ="np_viewtransaction.html">Retrieve Credit Transfer Transaction</a>.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceType</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is a Credit Transfer resource.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
            <td>The The <a href="np_separeasons.html">SEPA Reason Code</a> or the <a href="np_bacsreasons.html"> Bacs Reason Code</a> (depending on the scheme)</td>
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
	<td>Remittance information related to the transaction.</td>
</tr>


	</tbody>
</table>

## JSON Sample

The following is an example of a Credit Transfer Rejection event JSON:

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
    "eventType": "CreditTransferCancel",
	"resourceReference": "321-CTAB-234-GFT",
	"resourceReferenceType": "EndToEndId",
	"resourceUri": "/accounts/qj29pkgnbx/transactions/yabcdwgrg23",
	"resourceType": "Transaction",
	"reasonCode": "CUST",
	"resourceOwner": "tc47ygrg72",
	"resourceRemittanceInformation": null	
}</code>
</pre>

{% include links.html %}
