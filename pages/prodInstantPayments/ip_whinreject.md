---
title: Inbound Instant Payment Reject Event
keywords: Inbound Instant Payment Reject Event 
summary: "An Inbound Instant Payment is set to Rejected status"
sidebar: ip_sidebar
permalink: ip_whinreject.html
folder: prodInstantPayment
toc: false
---
 
{% include webhook.html content="A formal notification from the CSM for the negative confirmation message dispatched from Origix IP." %}


## Webhook Message Details

This Webhook has a single event type: <b>InstantCreditTransferReject</b>



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
			<td>InstantCreditTransferReject</td>
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
            <td>This is the URI of the resource for RESTful API querying. Use this URI to <a href="ip_retrieveinstct.html">Retrieve Instant Payment</a>.</td>
		</tr>
		<tr>
			<td>resourceDetails</td>
			<td>type</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is an 'InstantCreditTransfer' resource.</td>
		</tr>
		<tr>
			<td>resourceDetails</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
			<td>The <a href="ip_separeasons.html">Reason Code</a> returned.</td>
		</tr>
		
	</tbody>
</table>


## JSON Sample

The following is an example of an ``InstantCreditTransferReject`` event JSON:

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
	  "eventTimestamp":1529515551496,
	  "eventType":"InstantCreditTransferReject",
	  "resourceTechnicalId":53,
	  "resourceReference":"TxID001",
	  "resourceReferenceType":"TransactionId",
	  "resourceDetails":
		{  
		  "uri":"/instantpayments/j6p2lj7bvy",
		  "type":"InstantCreditTransfer",
		  "reasonCode":"FF01"
		}
}



</code>
</pre>



{% include links.html %}
