---
title: Mandate Reject Event
keywords: Mandate/DDI Cancel Event Webhook
summary: "Direct Debit Intruction Reject Webhook event"
sidebar: np_sidebar
permalink: np_whmandreject.html
folder: prodNuapay
toc: false
---

{% include webhook.html content="An AUDDIS rejection is processed resulting in a DDI transitioning from EXPORTED to REJECTED status. This event only impacts DDIs created in the Bacs scheme." %}

{% include tip.html content="This Webhook notification is currently only available in our Sandbox environment." %}

A Direct Debit Instruction (mandate) created under Bacs:
* Must be passed to the scheme to be approved before collections may be made against it.
* Where the DDI is not approved (e.g. the payer's account does not allow Direct Debit payments), the scheme will inform Nuapay via an Automated Direct Debit Instruction Service (AUDDIS) notification. A specific [AUDDIS error code](np_bacsreasons.html#auddis-reason-codes) is assigned.
* Nuapay will set the [DDI status](np_mandatestatuses.html) to `REJECTED`.

## Webhook Message Details

This Webhook has the following event types:

|**Webhook Event Type**| **Description**|
|MandateReject|Nuapay may be notified by the scheme of a rejection of a DDI. Once processed, Nuapay will trigger this notification, provided the partner/merchant has been configured to receive it.|


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
            <td><b>MandateReject</b></td>
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
			<td>resourceType</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is a mandate resource.</td>
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
		<tr>
			<td>root</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>Optional</td>
            <td>The <a href="np_bacsreasons.html#auddis-reason-codes">Reason code</a> as assigned during the AUDDIS import.</td>
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
    "eventType": "MandateReject",
	"resourceReference": "MY-UNIQUE-MANDATE-REF",
	"resourceReferenceType": "MandateReference",
	"resourceUri": "/schemes/p2lqa394mv/mandates/awtc1ebd",
	"resourceType": "Mandate",
	"resourceOwner": "tc47ygrg72",
	"resourceRemittanceInformation": null,
	"reasonCode": B
}</code>
</pre>

{% include links.html %}
