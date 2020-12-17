---
title: Payment Schedules Overview
keywords: Payment Schedules Overview
summary: "With Payment Schedules you can set up a series of Direct Debit payments to be collected over a configurable period of time or over an open-ended term."
sidebar: np_sidebar
permalink: np_schedulesoverview.html
folder: prodNuapay
---


Payment Schedules allow you to set up a series of payments against a mandate/DDI. Schedules can be Fixed-Length or Open-Ended.

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
<li>Amount of the Direct Debit payment.</li>
<li>Frequency of the Direct Debit payments.</li>
<li>Total number of payments.</li>
<li>Direct Debits are created when the schedule is created.</li>
</ul>
With a fixed-length schedule, the total number of required payments are created in <code>READY FOR EXPORT</code> <a href = "np_ddstatuses.html">status</a>. The latest payment is exported (i.e. sent to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing</a> or to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.bacs-clearing}}">Bacs Clearing</a>, depending on your selected scheme) automatically as each payment in the schedule is due.
</td>
</tr>
<tr>
<td>Open-Ended</td>
<td>In an open-ended schedule the:<br/>
<ul>
<li>Direct Debit amount is specified.</li>
<li>Frequency is required.</li>
<li>Number of payments <i>is not defined</i>.</li> 
<li>Payments will continue to be made indefinitely.</li>
</ul>
Only one payment (the latest) is ever in <code>READY_FOR_EXPORT</code> status prior to its collection date. The payment is exported (i.e. sent to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing</a> or to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.bacs-clearing}}">Bacs Clearing</a>, depending on your selected scheme) automatically and a new Direct Debit is created in READY_FOR_EXPORT.
</td>
</tr>
</tbody>
</table>

A schedule may be configured with any one of the following frequencies:

* Daily
* Weekly
* Bi-weekly
* Monthly
* Yearly
* Custom

The *Custom* option allows you to make collections at intervals of every: 

* 3 months (quarterly) or
* 6 months (bi-anually). 

Where you choose the custom option you must set `paymentCustomFrequency` = 3 or 6 in the [Create Payment Schedule](np_createschedule.html) or in the [Create Payment Schedule & Mandate](np_createschedulemandate.html) endpoints.

{% include links.html %}
