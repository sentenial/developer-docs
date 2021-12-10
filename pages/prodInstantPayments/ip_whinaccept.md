---
title: Inbound Instant Payment Accepted Event
keywords: Inbound Instant Payment Accepted Event
summary: "An inbound Instant Payment is set to Accepted status"
sidebar: ip_sidebar
permalink: ip_whinaccept.html
folder: prodInstantPayment
toc: false
---

{% include webhook.html content="A formal notification from the CSM for the positive confirmation message dispatched from Origix IP." %}

{% include wh-compatibility.html %}

## Webhook Message Details

This Webhook has a single event type: <b>InstantCreditTransferCSMAccept</b>


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
			<td>InstantCreditTransferCSMAccept</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceTechnicalId</td>
			<td>number</td>
			<td>Mandatory</td>
            <td>Technical identifier</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceReference</td>
			<td>string</td>
			<td>optional</td>
			<td>The Instant Payment Transaction ID</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceReferenceType</td>
			<td>string</td>
			<td> optional</td>
			<td>Set to TransactionId'</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceUri</td>
			<td>string</td>
			<td>Mandatory</td>
            <td>This is the URI of the resource for RESTful API querying. Use this URI to <a href="ip_retrieveinstct.html">Retrieve Instant Payment</a>.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceType</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is an 'InstantCreditTransfer' resource.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
			<td>Always null for Accepted Instant Payments. </td>
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

The following is an example of an Accepted inbound Instant Payment ``InstantCreditTransferCSMAccept`` event JSON:

<b>Headers</b>:


|POST| http://example.com/webhooks|
|Content-Type:| application/json;charset=UTF-8|
|X-Signature: |123ab01d030dee864fb44cc65a3be52ae591f46cde8d14d3e72fbc3790e4a304|
|Content-Length:| 261|
|X-Request-Id:| dc645679-71a5-498d-bb29-ec027948c7c1|

<b>JSON Request Body</b>
<pre>
<code class="json">

{  
    "eventTimestamp":1529515534903,
    "eventType":"InstantCreditTransferCSMAccept",
    "resourceTechnicalId":50,
    "resourceReference":"TxID001",
    "resourceReferenceType":"TransactionId",
    "resourceUri":"uri":"/instantpayments/wqj29nnmxn",
    "resourceType":"InstantCreditTransfer",
    "reasonCode":null,
    "resourceOwner": "tc47abc73",
    "resourceRemittanceInformation": null
}


</code>
</pre>



{% include links.html %}
