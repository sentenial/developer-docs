---
title: Open Banking Payment Refunded Event
keywords: Payment Refunded Event Webhook
summary: "Payment Refunded Webhook event"
sidebar: ob_sidebar
permalink: ob_whrefundcomplete.html
folder: prodOpenBanking
toc: false
---

{% include webhook.html content="A refunded payment has been successfully credited to the PSU. The associated refund object has a status of REFUND_COMPLETE." %}

{% include wh-compatibility.html %}

## Webhook Message Details

This Webhook has a single event type: <b>PaymentRefundComplete</b>

{% include tip.html content="For [Developer Dashboard](wh_config_ui.html#setting-up-a-webhook) users: select the **Open Banking Refund Complete** event." %}


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
			<td>PaymentRefundComplete</td>
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
			<td> This is URI of the refund resource. Use the URI in the <a href="ob_retrievepayment.html">Retrieve Payment</a> call.</td>
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
			<td>This is the type of the resource to which the URI is related. In this case it is a refund resource.</td>
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
    "eventType": "PaymentRefundComplete",   
    "resourceReference": "null",
    "resourceReferenceType": "reference",    
    "resourceUri": "/payments/n7rklmvtjc/refunds/mfc672erts",
    "resourceId": "mfc672erts",
    "resourceType": "null",
    "reasonCode": null,
    "resourceOwner": "tc47ygrg72",
    "resourceRemittanceInformation": null     
}</code>
</pre>

## Differences in EUR and GBP Remittance Information

* Remittance information is handled differently for GBP and EUR transactions.
* See the [Remittance Information](ob_refundpayment.html#remittance-information) section under the [Refund Payment](ob_refundpayment.html) for more on this.
* Depending on the currency of the original transaction, the Webhook notification varies:

**GBP Message Sample**:

Where the following remittance information is returned in the response from the initial refund request:

<pre>
<code class="json">
"remittanceInformation": {
            "reference": "reference",
            "unstructured": null
        },
</code>
</pre>

The Webhook message returns the remittance as follows:

<pre>
<code class="json">{
  "eventTimestamp": 1716323062000,
  "eventType": "PaymentRefundComplete",
  "resourceReference": "reference",
  "resourceReferenceType": "EndToEndId",
  "resourceUri": "/payments/w6be49w52y/refunds/w6bejzqp2y",
  "resourceId": "w6bejzqp2y",
  "resourceType": "refund",
  "reasonCode": null,
  "resourceOwner": "8b5jaky82r",
  "resourceRemittanceInformation": "reference"
}
</code>
</pre>

Note that:
* The `resourceReferenceType` is flagged as `EndToEndId`
* For GBP transactions, this is the transaction reference and not an End-to-End identifier.

**EUR Message Sample**:

Where the following remittance information is returned in the response from the initial refund request:

<pre>
<code class="json">

"remittanceInformation": {
            "reference": null,
            "unstructured": "remittanceInformation.unstructured"
        }
</code>
</pre>

The Webhook message returns the remittance as follows:

<pre>
<code class="json">{
  "eventTimestamp": 1716322382000,
  "eventType": "PaymentRefundComplete",
  "resourceReference": "v0hlvm56k000000000",
  "resourceReferenceType": "EndToEndId",
  "resourceUri": "/payments/zrmp73dlm6/refunds/zrmp86qy26",
  "resourceId": "zrmp86qy26",
  "resourceType": "refund",
  "reasonCode": null,
  "resourceOwner": "p2lj6g5abv",
  "resourceRemittanceInformation": "remittanceInformation.unstructured"
}</code>
</pre>

{% include links.html %}
