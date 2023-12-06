---
title: Open Banking Payment Declined Event
keywords: Payment Declined Event Webhook
summary: "Payment Declined Webhook event"
sidebar: ob_sidebar
permalink: ob_whpaymentdecl.html
folder: prodOpenBanking
toc: false
---

{% include webhook.html content="The PSU has declined to authorise a payment at the ASPSP." %}

{% include wh-compatibility.html %}

## Webhook Message Details

This Webhook has a single event type: <b>PaymentDeclined</b>

{% include tip.html content="For [Developer Dashboard](wh_config_ui.html#setting-up-a-webhook) users: select the **Open Banking Declined Credit Transfer** event." %}


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
			<td>PaymentDeclined</td>
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
			<td> This is URI of the payment resource. Use the URI in the <a href="ob_retrievepayment.html">Retrieve Payment</a> call.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceType</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is a payment resource.</td>
		</tr>
        <tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
			<td>Null </td>
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

The following is an example of a Received Payment event JSON:

<b>Headers</b>:


|POST| http://example.com/webhooks|
|Content-Type:| application/json;charset=UTF-8|
|[x-signature](wh_receivingep.html#x-signature): |123ab01d030dee864fb44cc65a3be52ae591f46cde8d14d3e72fbc3790e4a304|
|Content-Length:| 261|
|X-Request-Id:| dc645679-71a5-498d-bb29-ec027948c7c1|

<b>JSON Request Body</b>
<pre>
<code class="json">{
    "eventTimestamp": 1501169079000,
    "eventType": "PaymentDeclined",    
    "resourceReference": "42f8c5e2326f8b4c0563",
    "resourceReferenceType": "reference",    
    "resourceUri": "/payments/l5rklmvjsc",
    "resourceType": "payment",
    "reasonCode": null,
    "resourceOwner": "tc47ygrg72",
    "resourceRemittanceInformation": null
}</code>
</pre>



{% include links.html %}
