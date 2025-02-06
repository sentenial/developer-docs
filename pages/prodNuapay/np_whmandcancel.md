---
title: Mandate Cancel Event
keywords: Mandate/DDI Cancel Event Webhook
summary: "Direct Debit Intruction cancel Webhook event"
sidebar: np_sidebar
permalink: np_whmandcancel.html
folder: prodNuapay
toc: false
---

{% include webhook.html content="A Direct Debit Instruction (mandate) that was ACTIVE moves to CANCELLED status following a notification from the Scheme. This event only impacts DDIs created in the Bacs scheme." %}

{% include wh-compatibility.html %}

## Webhook Message Details

This Webhook has the following event types:

|**Webhook Event Type**| **Description**|
|MandateCancel|Nuapay may be notified by the scheme of a cancellation of a DDI. In this scenario a payer has gone to his/her bank and requested that the Direct Debit Instruction be cancelled so that funds may no longer be debited from his/her account. Bacs issue a notification file, referred to as an ADDACS, to notify of cancelations. Once processed, Nuapay will update the DDI status to CANCELLED and trigger this notification, provided the partner/merchant has been configured to receive it.|

The full list of possible cancellation reasons is provided under [ADDACS Reason Codes](np_bacsreasons.html#addacs-reason-codes).

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
            <td><b>MandateCancel</b></td>
		</tr>		
		<tr>
			<td>root</td>
			<td>resourceReference</td>
			<td>string</td>
			<td>optional</td>
			<td>This is the business reference of the resource (the Mandate ID/unique mandate/DDI reference).</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceReferenceType</td>
			<td>string</td>
			<td> optional</td>
			<td>This is set to MandateReference for this message.</td>
		</tr>		
		<tr>
			<td>root</td>
			<td>resourceUri</td>
			<td>string</td>
			<td>Mandatory</td>
			<td> This is URI of the resource allowing you to query the mandate details. See <a href ="np_retrievemandate.html">Retrieve Mandate</a>.</td>
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
			<td>This is the type of the resource to which the URI is related. In this case it is a mandate resource.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>Optional</td>
            <td>The <a href = "np_bacsreasons.html#addacs-reason-codes">Reason code</a> as assigned during the ADDACS import.</td>
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

The following is an example of an electronic mandate signing event JSON:

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
    "eventType": "MandateCancel",
	"resourceReference": "MY-UNIQUE-MANDATE-REF",
	"resourceReferenceType": "MandateReference",
	"resourceUri": "/schemes/p2lqa394mv/mandates/ltc1ebd",
	"resourceId": "ltc1ebd",
	"resourceType": "Mandate",
	"reasonCode": 2,
	"resourceOwner": "tc47ygrg72",
	"resourceRemittanceInformation": null	
}</code>
</pre>
{% include links.html %}
