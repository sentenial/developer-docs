---
title: Beneficiary Update Event
keywords: Beneficiary Update Event Webhook
summary: "Beneficiary Update Webhook event"
sidebar: ct_sidebar
permalink: np_whctbenefupdate.html
folder: prodNuapay
toc: false
---

{% include webhook.html content="Update of Beneficary details following the receipt of a notification from the beneficiry's bank (Bacs only)." %}

{% include wh-compatibility.html %}

## Webhook Message Details

This Webhook has just one event type: <b>BeneficiaryAccountUpdate</b>.

|This Webhook is only possible for **Bacs (GBP) beneficiaries** and is triggered when an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.awacs}}">AWACS</a> notification is received from Bacs.|

Following a beneficiary update, when you [Create a Credit Transfer](np_createct.html) payment, the `201 Created` response will include:

* The new (updated account details) in the `beneficaryAccount` object.
* The old beneficiary account details in the `originalBeneficiaryAccount` object.


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
			<td>BeneficiaryAccountUpdate</td>
		</tr>		
		<tr>
			<td>root</td>
			<td>resourceReference</td>
			<td>string</td>
			<td>optional</td>
			<td>This is set to the beneficiary's name.</td>
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
			<td> This is URI of the resource for RESTful API querying. Use the URI in the <a href="np_retrievect.html">Retrieve Credit Transfer</a> call.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>resourceType</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is a Beneficiay resource.</td>
		</tr>
		<tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
			<td>Null for beneficiaries. </td>
		</tr>
        <tr>
			<td>root</td>
			<td>resourceOwner</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the identifier of the merchant resource to which this notification is linked.</td>
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
    "eventTimestamp": 1501169079000,
    "eventType": "BeneficiaryAccountUpdate",
    "resourceReference": "John Smith",
    "resourceReferenceType": "beneficiaryName",
    "resourceUri": "/beneficiary/ybo8zayk2q",
    "resourceType": "beneficiary",
    "reasonCode": null,
    "resourceOwner": "tc47ygrg72"

}</code>
</pre>

{% include tip.html content="Webhook URIs do not include a version number. If you are attempting to retrieve a specific resource via a v2 API, please make sure to include the full `v2` path in your request." %}


{% include links.html %}
