---
title: Create Account
keywords: Create Account
summary: "Create Account RESTful API"
sidebar: np_sidebar
permalink: np_createaccount.html
folder: prodNuapay
toc: true
---

## API Details

The Create Account request allows you to generate a new Nuapay account.

* You may create a current account or (optionally and depending on your merchant configuration) a sub-account.
* EUR and GBP accounts are supported.

{% include important.html content="It is possible to generate a Master or a Sub-Account. Note that sub-accounts may only be used for processing Credit Transfer payments. Note too that your merchant must be configured by Nuapay Client Services team to allow you to create a sub-account. For more information please contact your Account Manager." %}

{% include idempotency.html %}

## EUR Account Creation

To create a **EUR** account:

* Specify `currency` = EUR (mandatory).
* You must also provide a `name` (mandatory).
* Optionally provide other values as required.
* On a successful 201 response the account is generated and the account status = `ACTIVE`

When generating EUR accounts, the IBAN is created immediately; the IBAN is always provided in a 201 response.  

## GBP Account Creation

To create a **GBP** account:

* Specify `currency` = GBP (mandatory).
* You must also provide a `name` (mandatory).
* Optionally provide other values as required.
* On a successful 201 response the account object is created and the account status will typically move to `PENDING`.
* The `identification` object in the response body will not contain any account details initially.
* GBP acount generation is asynchronous: the account creation logic for our GBP accounts requires that a call is passed to our partner GBP bank. So unlike EUR account creation, the account details are not available immediately, following a 201 response.
* Once the IBAN is created at our partner bank and returned to Nuapay, the account status moves to `ACTIVE`.

## Confirming the Account Status

After creating your GBP account (and retrieving a `PENDING` status), to determine the current status:

* Call the [View Account](np_viewaccount.html) endpoint.
* Pass the `accountId`
* Confirm the status in the `data` > `status` object.

{% include tip.html content="GBP accounts will typically transition from PENDING to ACTIVE in a matter of seconds." %}


## Account Statuses

The following account statuses are possible:

|**Status**|**Description**|
|`PENDING`| **GBP accounts only**: the Create Account request has been successful but an IBAN has not yet been generated.|
|`ACTIVE`| The account is live and may be used for payment processing.|
|`CLOSED`| The account is closed; no processing is possible and the account cannot be reactivated.|
|`SUSPENDED`| Processing is not possible but the account may be reactivated.|
|`ERROR`| There has been a problem with the account generation. Please contact Nuapay Support for assistance.|

An account must be in `ACTIVE` status to perform payment processing.



{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addAccountUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>
{% include links.html %}
