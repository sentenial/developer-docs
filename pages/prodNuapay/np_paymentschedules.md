---
title: Payment Schedules
keywords: Payment Schedules
summary: "Create a series or schedule of payments."
sidebar: np_sidebar
permalink: np_paymentschedules.html
folder: product2Nuapay
toc: false
---


## Payment Schedules

Direct Debit payments may be single, once-off payments but more typically they are grouped together so that a series, or **schedule**, of payments can be set up in one go.

For example:
* A magazine is published monthly.
* A payer signs up to a 12-month subscription.  
* Collections of €5 are taken via Direct Debit each month. 
* €60 is collected in total over the course of a single year (12 x €5).

Nuapay provides two payment schedule options:

1. Fixed Length
1. Open-ended

A fixed-length schedule might be useful where there are a specific set of payments required (e.g. a 12-month magazine subscription, as described above). 
An open-ended schedule would be more suited to a service where there is no defined end to the subscription, e.g. a music subscription service. 

<table>
<thead>
<tr>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Fixed-Length</td>
<td>In a fixed-length schedule you must specify the:<br/>
<ul>
<li>Amount of the Direct Debit collection.</li>
<li>Frequency of the Direct Debit payments.</li>
<li>Total number of payments.</li>
<li>Direct Debits are created when the schedule is created, all in READY_FOR_EXPORT status.</li>
</ul>
</td>
</tr>
<tr>
<td>Open-Ended</td>
<td>In an open-ended schedule the:<br/>
<ul>
<li>Direct Debit amount is specified.</li>
<li>Frequency is required.</li>
<li>Number of payments _is not defined_.</li> 
<li>Payments will continue to be made indefinitely.</li>
<li>One payment is created in READY_FOR_EXPORT; once that payment is exported, a new payment is created.</li>
</ul>
</td>
</tr>
</tbody>
</table>


{% include links.html %}
