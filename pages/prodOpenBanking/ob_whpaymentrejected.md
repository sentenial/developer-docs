---
title: Open Banking Payment Rejected Event
keywords: Payment Rejected Event Webhook
summary: "Payment Rejected Webhook event"
sidebar: ob_sidebar
permalink: ob_whpaymentrejected.html
folder: prodOpenBanking
toc: false
---

{% include webhook.html content="An Open Banking payment moves to SETTLEMENT_REJECTED status." %}

{% include wh-compatibility.html %}

## Webhook Message Details

This Webhook has a single event type: <b>PaymentRejected</b>

{% include tip.html content="For [Developer Dashboard](wh_config_ui.html#setting-up-a-webhook) users: select the **Open Banking Rejected Credit Transfer** event." %}


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
			<td>PaymentRejected</td>
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
			<td>This is the type of the resource to which the URI is related. In this case it is a payment resource.</td>
		</tr>
        <tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>Returns one of the following, based on the reason for the rejection:
			<ul>
			<li>PIS01 - SETTLEMENT_REJECTED</li>
			<li>PIS01 - CONSENT_API_REJECTED</li>
			<li>PIS01 - UNEXPECTED_ERROR</li>
			</ul>
			<strong>SETTLEMENT_REJECTED</strong> - indicates that there was an issue with the settlement.<br>
			<strong>CONSENT_API_REJECTED</strong> - indicates that the reject occurred because the bank was not available.<br>
			<strong>UNEXPECTED_ERROR</strong> - generated where there is a communication issue between TPP and the bank.
			<br><br>See <a href="ob_paymentstatuses.html">Payment Statuses</a> for more information on payment transitions.
			</td>
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
    "eventType": "PaymentRejected",    
    "resourceReference": "93t8f5g234rg8b4d16473r",
    "resourceReferenceType": "reference",    
    "resourceUri": "/payments/rp8klmvcmq",
    "resourceId": "rp8klmvcmq",
    "resourceType": "payment",
    "reasonCode": "PIS01 - SETTLEMENT_REJECTED",
    "resourceOwner": "tc47ygrg72",
    "resourceRemittanceInformation": null   
}</code>
</pre>



{% include links.html %}
