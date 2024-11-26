---
title: List Account Balances
keywords: List Account Balances API
summary: "List Account Balances RESTful API"
sidebar: acc_sidebar
permalink: np_listaccountbals.html
folder: prodNuapay
toc: false
---

## API Details

Use this request to return the balance on a specific account.
The response will return two balance amounts:

* BOOKED_BALANCE - the balance on the account at a given point in time.
* AVAILABLE_BALANCE - the balance amount that may be used to initiate Credit Transfer payments.

## Understanding Available Funds in the Balance Details API
Available Funds represent the amount that can be used from an account at any given time. These are calculated as:

|Available Funds = Booked Balance - Float - Balance Reservations|

Note that:
* Booked Balance: The total balance recorded in the account.
* Float: Funds that are temporarily unavailable e.g. an amount set aside to cover potential R-transactions..
* Balance Reservations: Amounts reserved for specific purposes, such as maintaining a minimum balance.

## How Reservations Work

Reservations may be in place in order to:
* Maintain a minimal balance requirements.
* Hold the required funds for Credit Transfers to be executed.

Pending payments do not block funds. However, funds are temporarily reserved during the processing phase to ensure account stability, verify sufficient balance, and prevent overdrafts.

## Behavior During Payment Processing

**Standard Payments**:

* Funds are checked and reserved at the moment the CT is created, ensuring enough funds are available and preventing parallel transactions from causing negative balances.
* For payments in a `READY_FOR_EXPORT` status, the reservation period is extremely short (approximately 1 second), so the difference between the Booked Balance and Available Funds is negligible.

**Express Payments**:

* Reservations last slightly longer, as they depend on receiving an acknowledgment from the payment scheme. However, this duration remains brief.

##Key Points

* Reservations ensure safe and consistent fund management during transaction processing.
* Pending payments do not affect the available balance.
* Differences between Booked Balance and Available Funds are typically minimal and transient, particularly for standard payments.

{% include note.html content="This request uses the `dateuntil` parameter. This takes a Unix Epoch timestamp and defaults to the current date" %}

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/viewAccountBalancesUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
