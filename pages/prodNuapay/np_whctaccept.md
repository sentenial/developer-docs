---
title: Credit Transfer Accept Event
keywords: Credit Transfer Accept Event Webhook
summary: "Credit Transfer Accept Webhook event"
sidebar: np_sidebar
permalink: np_whctaccept.html
folder: prodNuapay
toc: false
---

{% include webhook.html content="A Credit Transfer transaction transitions to ACCEPTED status on its execution date." %}


## Webhook Message Details

This Webhook has a single event type: **CreditTransferAccept**

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
            <td><b>CreditTransferAccept</b> </td>
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
			<td>resourceOwner</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the identifier of the merchant resource to which this notification is linked.</td>
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
		<tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
            <td>The The <a href="np_separeasons.html">SEPA Reason Code</a> or the <a href="np_bacsreasons.html"> Bacs Reason Code</a> (depending on the scheme)</td>
		</tr>

	</tbody>
</table>

## JSON Sample

The following is an example of a Credit Transfer Accept event JSON:

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
    "eventType": "CreditTransferAccept",
	"resourceReference": "341-CTCD-264-ABC",
	"resourceReferenceType": "EndToEndId",
	"resourceUri": "/accounts/qj29pkgnbx/transactions/yabcdwgrg23",
	"resourceType": "Transaction",
	"resourceOwner": "tc47ygrg72",
	"resourceRemittanceInformation": "PAYMENT RE: ABC",
	"reasonCode": null
}</code>
</pre>


{% include links.html %}
