---
title: Bacs Direct Debit Indemnity Claim Event
keywords: Direct Debit Indemnity Claim Event Webhook
summary: "Bacs Direct Debit Indemnity Claim Advice Webhook event"
sidebar: np_sidebar
permalink: np_whddicaevent.html
folder: prodNuapay
---

{% include webhook.html content="A DDICA file is imported into Nuapay, indicating that a Direct Debit Indemnity Claim Advice has been received from Bacs." %}


## Webhook Message Details

{% include tip.html content="This Webhook is only applicable to Bacs clients, processing GBP Direct Debits. " %}


This Webhook notifies you that a payer has sought a refund for a previously-settled Direct Debit payment.

Note that:
* The payer's bank will initially refund the payer in the event of an error in the payment of a Direct Debit by you, the merchant (the Service User in Bacs terminology).
* The payer's bank then use the indemnity claim process to recover the refunded payment from you, the merchant.
* An indemnity claim can only be raised for the full amount of the original Direct Debit payment.
* This Webhook notifies you that a claim has been initiated.
* The value of the Direct Debit is not debited immediately, you have the option to contest the claim, if you feel that you debited the payment in good faith and did not breach any Bacs guidelines in taking the payment.
* Bacs allows you a number of business days to contest the claim.
* If you are unsuccessful in contesting the claim, the value of the Direct Debit will be automatically debited from your account on Day 14 (this Webhook will be received on Day 1). (Each "Day" is a working day)

For more on the possible refund reasons and the challenges available, see [DDIC Reason Codes](np_bacsreasons.html#ddic-reason-codes).

|We also recommend that you contact your Account Manager who will be able to assist you with the challenge process.|

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
			<td>IndemnityClaimReceived</td>
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
			<td> string</td>
			<td>Mandatory</td>
			<td>This is URI of the resource for RESTful API querying; a Direct Debit URI. You can use this to query the resource with a <a href="np_retrievedirectdebit.html">Retrieve Direct Debit</a> call for example. </td>
		</tr>		
		<tr>
			<td>root</td>
			<td>resourceType</td>
			<td>string</td>
			<td>Mandatory</td>
			<td>This is the type of the resource to which the URI is related. In this case it is a Direct Debit resource.</td>
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
			<td>optional</td>
            <td> The <a href="np_bacsreasons.html#ddic-reason-codes"> Bacs DDIC Reason Code</a></td>
		</tr>		
	</tbody>
</table>


## JSON Sample

The following is an example of a Direct Debit Indemnity Claim Received event JSON:

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
    "eventType": "IndemnityClaimReceived",
	"resourceReference": "MAND12345abcdefd",
	"resourceReferenceType": "EndToEndId",
	"resourceUri": "/schemes/p2lqa394mv/mandates/lbyjxj5ebd/directdebits/a2rexnvdmq",
	"resourceType": "DirectDebit",
	"resourceOwner": "tc47ygrg72",
	"resourceRemittanceInformation": null,  
	"reasonCode": "8"
}</code>
</pre>

{% include links.html %}
