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

Your Available Balance is affected by:

* Any float that may be applied to your account.
* Where a minimum reserve balance has been applied to your account.
* Any future dated payments (in READY FOR EXPORT status).

## Standard SEPA CT

Taking an example of a future-dated SCT payment, the following describes how the balances are treated:

* An Account initially has a `BOOKED_BALANCE` = €1,000.00; `AVAILABLE_BALANCE` = €1,000.00
* A Credit Transfer for €400.00 is created with an execution date = _tomorrow_.
* When the payment is created it has an initial [status](np_ctstatuses.html) = PENDING (i.e. it is not immediately debited from the account and credited to the beneficiary); at 02:00 the transaction is processed and moves to READY_FOR_EXPORT status: a reserve (or hold) is placed on the funds.
* After creating this payment, `BOOKED_BALANCE` = €1,000.00; `AVAILABLE_BALANCE` is now = €600.00.  

Note that:
* At this point, €1,0000.00 is still credited on the account (the `BOOKED_BALANCE`)
* €400.00 has been set aside for the payment that will be issued tomorrow.
* If you wanted to create a second Credit Transfer, at this point, you would only be able to create a payment up to a maximum value = €600.00 i.e. up to the total value of the `AVAILABLE_BALANCE`.
* Once the payment is successfully credited to the beneficiary on its execution date (_tomorrow_, in this example), the `BOOKED_BALANCE` is updated to €600.00.


{% include note.html content="This request uses the `dateuntil` parameter. This takes a Unix Epoch timestamp and defaults to the current date" %}

## Faster Payments (FPS)

For Faster Payments:

* The balance reservation is set at the time of execution.
* Future-dated FPS credit transfers have a status of `PENDING` and are processed on their execution date at 2:00AM.
* After the FPS credit transfer is triggered, a balance reservation is placed on the account and the credit transfer status is updated to `PENDING_SETTLEMENT`.
* The `BOOKED_BALANCE` and `AVAILABLE_BALANCE` are different while the account has credit transfers in `PENDING_SETTLEMENT` status.
* The balances are then aligned once all credit transfers transition to a final payment status [`ACCEPTED` or `REJECTED`].

{% include tip.html content="Because FPS is an Instant scheme with transactions typically being processed in seconds, `PENDING_SETTLEMENT` is a momentary status and you will generally be unaware of the difference in `BOOKED_BALANCE` and `AVAILABLE_BALANCE` when processing FPS." %}

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
