---
title: Mandate Signature Event
keywords: Mandate Signature Event Webhook
summary: "Mandate Signature Webhook event"
sidebar: np_sidebar
permalink: np_whmandsignature.html
folder: prodNuapay
toc: false
---

{% include webhook.html content="A mandate moves to ACTIVE status." %}

{% include wh-compatibility.html %}

## Webhook Message Details

This Webhook has the following event types:

|**Webhook Event Type**| **Description**|
|MandateElectronicSign|When an electronic mandate is created via Nuapay as Active or is transitioned from Pending to Active, or to Active from Exported (BACS), for all channel. BACS and SEPA included|
|MandatePaperActivation|When a non-electronic Mandate transitions from Pending to Active or to Active from Exported (BACS), including Mandate-on-the-fly (MOTF). BACS and SEPA included|
|MandateCreation|When a non-electronic Mandate created in Nuapay with a status of Active is created, including MOTF for all channels.|



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
            <td><b>MandateElectronicSign</b> <br/> or <br/> <b>MandatePaperActivation</b> <br/> or <br/> <b>MandateCreation</b></td>
		</tr>		
		<tr>
			<td>root</td>
			<td>resourceReference</td>
			<td>string</td>
			<td>optional</td>
			<td>This is the business reference of the resource (the Mandate ID/unique mandate reference).</td>
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
			<td>resourceType</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is a mandate resource.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
			<td>Null for mandates. </td>
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
|X-Signature: |123ab01d030dee864fb44cc65a3be52ae591f46cde8d14d3e72fbc3790e4a304|
|Content-Length:| 261|
|X-Request-Id:| dc645679-71a5-498d-bb29-ec027948c7c1|

<b>JSON Request Body</b>
<pre>
<code class="json">{
    "eventTimestamp": 1501169079000,
    "eventType": "MandateElectronicSign",
	"resourceReference": "MY-UNIQUE-MANDATE-REF",
	"resourceReferenceType": "MandateReference",
	"resourceUri": "/schemes/p2lqa394mv/mandates/lbyjxj5ebd",
	"resourceType": "Mandate",
	"reasonCode": null,
	"resourceOwner": "tc47ygrg72",
	"resourceRemittanceInformation": null	
}</code>
</pre>

{% include links.html %}
