---
title: End User Experience
keywords: sample
summary: "The end user (PSU) experience is described here. The user selects his/her bank and provides read access to a selected account "
sidebar: ver_sidebar
permalink: ver_psujourney.html
folder: prodNuapay
---


## Overview

To initiation a verification check:
1. You will call [POST /verification](ver_reqverification.html); specifying the customer’s name to be verified.
1. The verification request is generated in `PENDING` status and the response returns a `userInterfaceVerificationId`, which is used to launch the initial Overview screen, which will allow the customer to give consent to access his/her account.
1. Note that the flow may be initiated in `CHECKOUT` or `REDIRECT` mode – the client specifies the required option in the API request.

For more on this, see [Launching the Flow](ver_launch.html).

## Verification Steps

Having clicked the **Verify** button on the calling page:
1. The user initially sees an Overview screen:
<img src = "images/ver_overview.png">
1. Clicks <strong>Continue</strong> to advance to the Bank Selection screen:
<img src = "images/ver_selbanks.png">
1. The user selects a bank and is redirected to the bank’s logon page.
1. Alternatively, users may decide to continue the flow on a mobile device. To do this, they scan a QR code to launch their banking app on a mobile device.
1. Once successfully authenticated at the bank, the user is prompted to provide consent to the account access request. Only account information is retrieved.
1. Once successful, the end user is redirected to the confirmation screen:
<img src = "images/ver_confirm.png">
1. In the background, an API request (`PATCH /verification`) is called to update the verification request with the Consent ID.
1. A call is then passed to `GET /accounts` to retrieve the account name held at the customer's bank.

## Post-Verification

Once the steps are completed:
*	The customer has provided consent to allow the service to access his/her account details.
*	These account details are retrieved and, because 2-factor authentication has been required at the bank, merchants can be confident that the user is the legitimate owner of the account(s) at the bank.
*	Where a user has more than one account, the bank may allow him/her to select a specific account, or the user may just give a single consent to allow access to all accounts.
*	Where more than one account is available, a matching score for each is provided. see [Scoring](ver_scoring.html) for more.

{% include links.html %}
