---
title: Non-Processing Days
keywords: Working Days Business Days SEPA Bacs
summary: "In the SEPA and Bacs schemes certain days are configured as non-working or non-business days. On these days no payment or mandate processing is carried out. This section gives some extra details on these non-processing days."
sidebar: np_sidebar
permalink: np_businessdays.html
folder: prodNuapay
toc: false
---

## Overview

{% include note.html content="The Faster Payments (GBP) and SEPA Instant CT (EUR) schemes are always-on schemes, operating 24/7/365 so there are no non-processing days for those schemes." %} 


In both the SEPA and Bacs schemes (for both Direct Debit and Credit Transfer payments) the following are non-processing days:

* Saturdays
* Sundays

In addition, both schemes see other dates as being non-processing. For example:

* Christmas Day (December 25th)
* New Year's Day (January 1st)

However the schemes differ on other holidays and the following sections give an overview.

{% include note.html content="Where you specify a non-processing date as your collection date (for a Direct Debit payment) if `settlementDateShift` is set to true then the date will automatically be moved to the next available processing date." %} 

## SEPA Non-Processing Days

In SEPA the following are non-processing days:

|**Day**|**Date**|**Description**|
|New Year's Day| January 1st| If the day falls on a Saturday or Sunday it is not carried forward|
|Good Friday| Variable| Changes annually|
|Easter Monday| Variable | Changes annually|
|Labour Day| May 1st |If the day falls on a Saturday or Sunday it is not carried forward|
|Christmas Day| December 25th|If the day falls on a Saturday or Sunday it is not carried forward|
|Christmas Holiday| December 26th| If the day falls on a Saturday or Sunday it is not carried forward|

{% include tip.html content="Countries may have specific 'bank holidays', for example March 17th is St. Patrick's Day in Ireland, where banks are closed. These local holidays do not impact SEPA processing and March 17th is treated as a standard business day for SEPA processing in Ireland." %} 

## Bacs Non-Processing Days

The Bacs non-processing dates are published annually and are available on the Bacs Web site:

|**Year**|**Link**|
|2020|[https://www.bacs.co.uk/documentlibrary/bacs_processing_calendar_2020.pdf](https://www.bacs.co.uk/documentlibrary/bacs_processing_calendar_2020.pdf){:target="_blank"}|
|2021|[https://www.bacs.co.uk/documentlibrary/bacs_processing_calendar_2021.pdf](https://www.bacs.co.uk/documentlibrary/bacs_processing_calendar_2021.pdf){:target="_blank"}|


{% include links.html %}
