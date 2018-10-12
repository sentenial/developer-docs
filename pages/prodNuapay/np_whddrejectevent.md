---
title: Direct Debit R-Transaction Event
keywords: Direct Debit R-Transaction Event Webhook 
summary: "Direct Debit R-Transaction Webhook event"
sidebar: np_sidebar
permalink: np_whddrejectevent.html
folder: prodNuapay
---
 
{% include webhook.html content="A PAIN.002 reject file is imported into Nuapay updating a Direct Debit's [payment status](np_ddstatuses.html)." %}


## Webhook Message Details

This Webhook notifies you when a Direct Debit is updated to a Rejected status. 

The following event types are possible:

|**Webhook Event Type**| **Nuapay Direct Debit Status**|
|DirectDebitCancel|CANCELLED|
|DirectDebitRefuse|REFUSED|
|DirectDebitReturn|RETURNED|
|DirectDebitRefund|REFUNDED|

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
			<td> Allowed values are the Webhook Event Types referenced in the table above. </td>
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
			<td> This is URI of the resource for RESTful API querying; a Direct Debit URI. You can use this to query the resource with a <a href="np_retrievedirectdebit.html">Retrieve Direct Debit</a> call for example. </td>
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
            <td> The <a href="np_separeasons.html">SEPA Reason Code</a> </td>
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
    "eventType": "DirectDebitReject",
	"resourceReference": "Webhook1",
	"resourceReferenceType": "EndToEndId",
	"resourceUri": "/schemes/p2lqa394mv/mandates/lbyjxj5ebd/directdebits/a2rexnvdmq",
	"resourceType": "DirectDebit",
	"reasonCode": "MS03"
}</code>
</pre>

{% include links.html %}
