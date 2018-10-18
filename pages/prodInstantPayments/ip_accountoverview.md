---
title: Origix IP Account Overview
keywords: Account Overview Instant Payments Technical account
summary: "The Origix IP Technical account gives a view of the actual movements on your settlement account that the CSM uses when crediting and debiting funds."
sidebar: ip_sidebar
permalink: ip_accountoverview.html
folder: prodInstantPayments
---

{% include callout.html content="Note that this section is only relevant to Affilaite users who do not have direct access to the settlement account that is used by the CSM for settlement. If you will be accessing the Instant Payment scheme via a banking partner then this section is relevant to you.  " type="danger" %} 

Your Origix IP Technical account is a mirroring account and gives a view of the actual settlements that are taking place on the account held by your participant bank in the CSM.

There are two options available to you to view the details on your account:

1. Log on to Origix IP and view the account via the Accounts tab.
1. Access the account details via REST API.

## Technical Account - User Interface View

To view your account via the Origix IP user interface:

* Use the credentials provided to you during registration to log on to the Origix IP portal: https://origix.sentenial.com/origix/
* Select the Accounts tab
* Inbound and Outbound payments are listed along with remittance information, amount and balance.

<img src="images/sip_account_tab.png">

{% include important.html content="The Accounts tab allows you to search for transactions based on date range and payment value. Transactions may also be exported to CSV or Excel format." %}

## Technical Account - via API

If you would prefer to use an API to access your account information, rather than the Accounts tab user interface option, Origix IP offers the following REST calls:

* [List Account](ip_accountapilist.html)
* [List Transactions](ip_accountapilisttx.html)
* [View Transaction](ip_accountapiviewtx.html)

{% include note.html content="List Account is only required to retrieve the URI for your account; this URI is subsequently referenced in your calls to List and View Transaction." type="danger" %}

When using the API approach:
1. The ``List Transaction`` service will return a set of transactions within a defined date range.
1. Each returned transaction includes a unique URI to each transaction.
1. With a specific URI related to a transaction, ``View Transaction`` may be used to retrieve the details of that specific Instant Payment.

