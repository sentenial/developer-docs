---
title: List Account Balances
keywords: List Account Balances API
summary: "List Account Balances RESTful API"
sidebar: np_sidebar
permalink: np_listaccountbals.html
folder: prodNuapay
toc: false
---

## API Details

Use this request to return the balance on a specific account.
The response will return two balance amounts:

* BOOKED_BALANCE - the balance on the account at a given point in time.
* AVAILABLE_BALANCE - the balance amount that may be used to initiate Credit Transfer payments.

For example:
* An Account initially has a `BOOKED_BALANCE` = €1,000.00; `AVAILABLE_BALANCE` = €1,000.00
* A Credit Transfer for €400.00 is created with an execution date = _tomorrow_.
* When the payment is created it has an initial [status](np_ctstatuses.html) = PENDING (i.e. it is not immediately debited from the account and credited to the beneficiary); a reserve (or hold) is placed on the funds.
* After creating this payment, `BOOKED_BALANCE` = €1,000.00; `AVAILABLE_BALANCE` is now = €600.00.  

Note that:
* At this point, €1,0000.00 is still credited on the account (the `BOOKED_BALANCE`)
* €400.00 has been set aside for the payment that will be issued tomorrow.
* If you wanted to create a second Credit Transfer, at this point, you would only be able to create a payment up to a maximum value = €600.00 i.e. up to the total value of the `AVAILABLE_BALANCE`. 
* Once the payment is successfully credited to the beneficiary on its execution date (_tomorrow_, in this example), the `BOOKED_BALANCE` is updated to €600.00.


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
