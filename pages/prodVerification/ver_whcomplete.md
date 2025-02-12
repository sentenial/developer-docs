---
title: Verification Complete Event
keywords: Account Verification Complete Webhook
summary: "Account Verification Complete Webhook event"
sidebar: ver_sidebar
permalink: ver_whcomplete.html
folder: prodVerification
toc: false
---

{% include webhook.html content="An account verification check has moved to COMPLETE status." %}

{% include wh-compatibility.html %}

## Webhook Message Details

This Webhook has just one event type: <b>VerificationCompleted</b>


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
			<td>VerificationCompleted</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceReference</td>
			<td>string</td>
			<td>optional</td>
			<td>The business reference of the resource.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceReferenceType</td>
			<td>string</td>
			<td> optional</td>
			<td>This can be a business reference of the resource, useful when filtering events via the Webhooks area of the Nuapay Console.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceUri</td>
			<td>string</td>
			<td>Mandatory</td>
			<td> This is the URI of the verification resource. Use the URI in the <a href = 'ver_retrieveverification.html'>Retrieve Verification</a> call.</td>
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
			<td>This is the type of the resource to which the URI is related. In this case it is a verification resource.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
			<td>Null for this event. </td>
		</tr>
        <tr>
			<td>root</td>
			<td>resourceOwner</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the identifier of the merchant resource to which this event notification is linked.</td>
		</tr>
    <tr>
  <td>root</td>
  <td>resourceRemittanceInformation</td>
  <td>string</td>
  <td>optional</td>
  <td>Remittance information - null for this event type.</td>
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
  "eventTimestamp": 1727154185004,
  "eventType": "VerificationCompleted",
  "resourceReference": "a3vklmvfge",
  "resourceReferenceType": "verificationId",
  "resourceUri": "/verifications/a3vklmvfge",
  "resourceId": "a3vklmvfge",
  "resourceType": "Verification",
  "reasonCode": null,
  "resourceOwner": "tc47ygrg72",
  "resourceRemittanceInformation": null

}</code>
</pre>



{% include links.html %}
