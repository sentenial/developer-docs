---
title: Outbound Instant Payment Reject Event
keywords: Outbound Instant Payment Reject Event 
summary: "An outbound Instant Payment is set to Rejected status"
sidebar: ip_sidebar
permalink: ip_whoutreject.html
folder: prodInstantPayment
toc: false
---
 
{% include webhook.html content="A negative confirmation received from the CSM in response to an outbound SCT Inst instruction." %}


## Webhook Message Details

Possible Webhook event types: 

|**Webhook Event Type**|**Description**|
|InstantCreditTransferCSMReject| Rejected by the CSM|
|InstantCreditTransferBBReject| Rejected by the Beneficiary Bank|



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
			<td>InstantCreditTransferCSMReject OR InstantCreditTransferBBReject</td>
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
            <td>The <a href="ip_separeasons.html">Reason Code</a> returned. </td>
		</tr>
		
	</tbody>
</table>



{% include note.html content="the SCT Inst instruction may be rejected by the Beneficiary Bank or the CSM. Beneficiary Bank rejections are notified as InstantCreditTransferBBReject. This might be returned where the Beneficary's account is closed for example . Or it may be a failure at the CSM notified as an InstantCreditTransferCSMReject, where the payment was not received within the scheme time limits, for example." %}



## JSON Sample

The following is an example of an ``InstantCreditTransferCSMReject`` event JSON:

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
    "eventTimestamp":1529515562726,
    "eventType":"InstantCreditTransferCSMReject",
    "resourceTechnicalId":56,
    "resourceReference":"trxTest002",
    "resourceReferenceType":"TransactionId",
    "resourceUri":"/instantpayments/xgwbvn9m7r",
    "resourceType":"InstantCreditTransfer",
    "reasonCode":"AB06"
}


</code>
</pre>



{% include links.html %}
