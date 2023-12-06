---
title: Incoming Credit Transfer Event
keywords: Incoming Credit Transfer Event Webhook
summary: "Incoming Credit Transfer Webhook event"
sidebar: ct_sidebar
permalink: np_whincomingct.html
folder: prodNuapay
toc: false
---

{% include webhook.html content="Incoming Credit Transfer payment crediting the Nuapay IBAN." %}

{% include wh-compatibility.html %}

## Webhook Message Details

This Webhook has just one event type: <b>IncomingCreditTransfer</b>


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
			<td>IncomingCreditTransfer</td>
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
			<td> This is URI of the resource for RESTful API querying. Use the URI in the <a href="np_retrievect.html">Retrieve Credit Transfer</a> call.</td>
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
			<td>Null for Incoming Credit Transfers. </td>
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

The following is an example of an Incoming CT event JSON:

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
    "eventType": "IncomingCreditTransfer",
	"resourceReference": "EDS-1234-RFT-456-DEF-87",
	"resourceReferenceType": "EndToEndId",
	"resourceUri": "/accounts/qj29pkgnbx/transactions/ym37ygrg23",
	"resourceType": "Transaction",
	"reasonCode": null,
	"resourceOwner": "tc47ygrg72",
	"resourceRemittanceInformation": "PAYMENT FOR INVOICE 123ABC"

}</code>
</pre>


{% include links.html %}
