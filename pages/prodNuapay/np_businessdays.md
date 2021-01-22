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

In addition, the following are deemed to be non-processing days:

* Christmas Holidays (December 25th & 26th)
* New Year's Day (January 1st)
* Easter Holidays (Good Friday & Easter Monday)

However the schemes differ on other holidays as outlined in the table below.

## Non-Processing Days Overview

The following summarises the non-processing days applicable to both the SEPA and Bacs Direct Debit and Credit Transfer schemes:

|**Day**|**Date**|**Description**|**Scheme**|
|**New Year's Day**| January 1st| If the day falls on a Saturday or Sunday it is not carried forward in SEPA; for Bacs the next business day is taken. |SEPA & Bacs|
|**Good Friday**| Variable| Changes annually|SEPA & Bacs|
|**Easter Monday**| Variable | Changes annually|SEPA & Bacs|
|**Labour Day**| May 1st |If the day falls on a Saturday or Sunday it is not carried forward in SEPA; for Bacs the next business day is taken.|SEPA & Bacs|
|**Spring Bank Holiday**|Variable|Typically the last Monday in May |Bacs only|
|**Summer Bank Holiday**|Variable|Typically the last Monday in August|Bacs only|
|**Christmas Day**| December 25th|If the day falls on a Saturday or Sunday it is not carried forward in SEPA; for Bacs the next business day is taken.|SEPA & Bacs|
|**Christmas Holiday**| December 26th| If the day falls on a Saturday or Sunday it is not carried forward in SEPA; for Bacs the next business day is taken.|SEPA & Bacs|

{% include tip.html content="SEPA Countries may have specific 'bank holidays', for example March 17th is St. Patrick's Day in Ireland, where banks are closed. These local holidays do not impact SEPA processing and March 17th is treated as a standard business day for SEPA processing in Ireland." %} 

{% include note.html content="Where you specify a non-processing date as your collection date (for a Direct Debit payment) if `settlementDateShift` is set to true then the date will automatically be moved to the next available processing date. The API response will return the Requested Date and the Actual Date that will be applied after the date shifting. " %} 

## Bacs Non-Processing Days

Note that:
* As some holidays may fall on a Saturday or Sunday and get pushed to the next business day in any given year, it is important to verify the non-processing days from year to year.
* Some Bacs holidays are only applicable to Northern Ireland.
* Ad hoc dates may be added as non-processing dates, for example the Platinum Jubilee bank holiday planned for June 2022.

To confirm the exact dates for the Bacs holidays, please refer to the **Bacs Processing Calendar**, which is published annually and available on the Bacs Web site:

|**Year**|**Link**|
|2021|[https://www.bacs.co.uk/documentlibrary/bacs_processing_calendar_2021.pdf](https://www.bacs.co.uk/documentlibrary/bacs_processing_calendar_2021.pdf){:target="_blank"}|


{% include links.html %}
