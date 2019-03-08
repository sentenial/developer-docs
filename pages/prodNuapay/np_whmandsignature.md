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
			<td>resourceTechnicalId</td>
			<td>number</td>
			<td>Mandatory</td>
            <td>Unique identifier</td>
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
			<td> This is URI of the resource allowing you to query the mandate details. See <a href ="np_retrievemandate.html">Retrieve Mandate</a>.</td>
		</tr>
		<tr>
			<td>resourceDetails</td>
			<td>type</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is a mandate resource.</td>
		</tr>
		<tr>
			<td>resourceDetails</td>
			<td>reasonCode</td>
			<td>string</td>
			<td>optional</td>
			<td>Null for mandates. </td>
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
	"resourceReference": "Webhook1",
	"resourceReferenceType": "MandateId",
	"resourceUri": "/schemes/p2lqa394mv/mandates/lbyjxj5ebd",
	"resourceType": "Mandate",
	"reasonCode": null
}</code>
</pre>


{% include links.html %}
