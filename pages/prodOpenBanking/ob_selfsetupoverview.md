---
title: Self-Hosted Payment Page Setup
keywords: Self Hosted Payment Page Setup Javascript Add Open Banking Payment Page
summary: "Adding Open Banking (Self-Hosted mode) as a payment option to your Payment Page requires configuration as outlined below. In Self-Hosted mode you must develop your own user interface."
sidebar: ob_sidebar
permalink: ob_selfsetupoverview.html
folder: prodOpenBanking
toc: false
---

## Overview

{% include note.html content="This section is for users who want to use the **SELF_HOSTED** mode - see [Implementation Options](ob_pispimplementation.html) for more on this." %}

To add Open Banking to your payment page you will need to carry out the following steps:

1. Retrieve your API Key - contact our Client Support team if you do not have a key.
1. Get a token representing the required merchant. 
1. Call GET `/banks` to retrieve a list of all supported banks.
1. This will allow you to render a bank selection screen. 
1. Once your PSU selects a bank, pass the user's `bankId` along with `integrationType = SELF_HOSTED` and the `merchantPostAuthUrl` (this can be the partner or merchant URL) in the request.
1. This will return a payment id and the `aspspAuthUrl`, to which you can redirect your PSU.
1. The PSU is redirected to the ASPSP:
1. The TPP posts the payment ID to the partner/merchant URL (merchantPostAuthUrl).
1. At this point the payment flow is complete and the payment has been submitted.
1. You will need to poll the ASPSP for a final payment status. (Alternatively Webhooks may be used).


{% include links.html %}






