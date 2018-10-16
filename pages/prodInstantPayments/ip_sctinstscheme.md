---
title: SEPA CT Instant Scheme
keywords: Instant Payments API Rules
summary: "API requirements when working with Instant Payments."
sidebar: ip_sidebar
permalink: ip_sctinstscheme.html
folder: prodInstantPayments
---

Origix IP offers connectivity to the SEPA Credit Transfer Instant (SCT Inst) payments scheme.

This scheme:

* Offers a potential geographical scope of 34 European countries and territories.
* Unlike the SEPA Credit Transfer or SEPA Direct Debit schemes, the SEPA Credit Transfer Instant scheme is always open: 24 x 7 x 365.
* Currently has a maximum value of €15,000 for a single transaction .
* In general, funds are available on the beneficiary’s account in ten seconds maximum. However the scheme allows for a hard time-out deadline, to cover exceptional processing situations. In these exceptional cases, instructions will be processed up to 20 seconds after the Originator Bank has added a Time Stamp to the instruction.

The following image gives an overview of the basic SCT Inst processing flows:

<img src="images\sipFlowOverview.png">


<table style="width: 100%" class="TableStyle-Standard" cellspacing="0">
	<col class="TableStyle-Standard-Column-Regular" />
	<col class="TableStyle-Standard-Column-Regular" />
	<tbody>
		<tr class="TableStyle-Standard-Body-Row1">
			<td class="TableStyle-Standard-BodyE-Regular-Row1" style="font-weight: bold;background-color: #6495ed;">1</td>
			<td class="TableStyle-Standard-BodyD-Regular-Row1">Originator Bank receives an SCT Inst Instruction from the
Originator.</td>
		</tr>
		<tr class="TableStyle-Standard-Body-Row1">
			<td class="TableStyle-Standard-BodyE-Regular-Row1" style="font-weight: bold;background-color: #6495ed;">2</td>
			<td class="TableStyle-Standard-BodyD-Regular-Row1">The Originator Bank then sends the SCT Inst Transaction message
to the CSM of the Originator Bank.</td>
		</tr>
		<tr class="TableStyle-Standard-Body-Row1">
			<td class="TableStyle-Standard-BodyE-Regular-Row1" style="font-weight: bold;background-color: #6495ed;">3</td>
			<td class="TableStyle-Standard-BodyD-Regular-Row1">The CSM of the Beneficiary Bank Instantly sends the SCT Inst
Transaction message to the Beneficiary Bank. </td>
		</tr>
		<tr class="TableStyle-Standard-Body-Row1">
			<td class="TableStyle-Standard-BodyE-Regular-Row1" style="font-weight: bold;background-color: #6495ed;">4 </td>
			<td class="TableStyle-Standard-BodyD-Regular-Row1">The Beneficiary Bank sends the confirmation message to the CSM of
the Beneficiary Bank indicating that the Beneficiary Bank has received the SCT Inst Transaction and is able to process the transaction (positive confirmation) or cannot process it (negative confirmation)</td>
		</tr>
		<tr class="TableStyle-Standard-Body-Row1">
			<td class="TableStyle-Standard-BodyE-Regular-Row1" style="font-weight: bold;background-color: #40e0d0;">A</td>
			<td class="TableStyle-Standard-BodyD-Regular-Row1">
				<p>Clearing function of the CSM, based on the response in step 4:</p>
				<ul style="list-style-type: square;">
					<li value="1">Negative Confirmation - the CSM of the Beneficiary Bank passes on this confirmation message to the CSM of the Originator Bank. The CSM of the Originator Bank releases the reservation of Funds for the cover done between steps 2 and 3.</li>
					<li value="2">
						<p>Positive Confirmation - the CSM of the Beneficiary Bank notifies to the Beneficiary Bank that the message in step 4 has been successfully received; The CSM of the Beneficiary Bank initiates the final settlement processing for this specific SCT Inst transaction with the CSM of the Originator Bank.</p>
					</li>
				</ul>
			</td>
		</tr>
		<tr class="TableStyle-Standard-Body-Row1">
			<td class="TableStyle-Standard-BodyE-Regular-Row1" style="font-weight: bold;background-color: #40e0d0;">B</td>
			<td class="TableStyle-Standard-BodyD-Regular-Row1">The
Beneficiary Bank will inform the Beneficiary about the funds made available
to the Beneficiary. </td>
		</tr>
		<tr class="TableStyle-Standard-Body-Row1">
			<td class="TableStyle-Standard-BodyE-Regular-Row1" style="font-weight: bold;background-color: #6495ed;">5</td>
			<td class="TableStyle-Standard-BodyD-Regular-Row1">only when the Beneficiary Bank has sent a positive confirmation via
the message in step 4 and the Beneficiary Bank has the certainty that the
message under step 4 has been successfully delivered to the CSM of the
Beneficiary Bank, it Instantly Makes the Funds Available to the Beneficiary. The
Beneficiary Bank relies on the settlement certainty covered by the message in
step 3.</td>
		</tr>
		<tr class="TableStyle-Standard-Body-Row1">
			<td class="TableStyle-Standard-BodyE-Regular-Row1" style="font-weight: bold;background-color: #6495ed;">6</td>
			<td class="TableStyle-Standard-BodyD-Regular-Row1">the CSM of the Originator Bank Instantly reports to the Originator Bank
if the SCT Inst Transaction had been successful (or not). The basis for this report is the contents of the confirmation message in step 4
which the CSM of the Originator Bank had received via the CSM of the
Beneficiary Bank.</td>
		</tr>
		<tr class="TableStyle-Standard-Body-Row1">
			<td class="TableStyle-Standard-BodyE-Regular-Row1" style="font-weight: bold;background-color: #6495ed;">7</td>
			<td class="TableStyle-Standard-BodyD-Regular-Row1">Where the Originator Bank receives a negative confirmation about the
SCT Inst Transaction, which indicates that the Funds had not been Made
Available to the Beneficiary, the Originator Bank is obliged to Immediately
inform the Originator. The Originator Bank lifts the Reservation of the Amount
made in step 1.</td>
		</tr>
		<tr class="TableStyle-Standard-Body-Row1">
			<td class="TableStyle-Standard-BodyB-Regular-Row1" style="font-weight: bold;background-color: #40e0d0;">C</td>
			<td class="TableStyle-Standard-BodyA-Regular-Row1">Where the Originator Bank receives
a positive confirmation about the SCT Inst Transaction, it formally debits the
Payment Account of the Originator.
The Originator Bank informs the Originator about
the Funds Made Available to the Beneficiary, via a Wenhook notification.</td>
		</tr>
	</tbody>
</table>

For more information on this, see the <a href ="https://www.europeanpaymentscouncil.eu/document-library/rulebooks/2017-sepa-instant-credit-transfer-rulebook" target="_blank">EBA SCT Inst Rulebook</a>.


{% include links.html %}
