---
title: Payment Schedules Overview
keywords: Payment Schedules Overview
summary: "With Payment Schedules you can set up a series of Direct Debit payments to be collected over a configurable period of time or over an open-ended term."
sidebar: np_sidebar
permalink: np_schedulesoverview.html
folder: prodNuapay
---


Payment Schedules allow you to set up a series of payments against a mandate/DDI. Schedules can be Fixed-Length or Open-Ended.

|**Fixed-Length**| You can specify the amount to collect, how often the payments are taken and the total number of Direct Debits to be collected. With a fixed-length schedule, the total number of required payments are created in `READY FOR EXPORT` [status](np_ddstatuses.html). The payments are exported (sent to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing</a> or to <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.bacs-clearing}}">Bacs Clearing</a>, depending on your selected scheme) automatically as each payment in the schedule is due.|
|**Open-Ended**| The amount and the frequency is specified however there is no set number of payments and collections will continue to be made indefinitely. Only one payment (the latest) is ever in `READY_FOR_EXPORT` status prior to its collection date.|

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
