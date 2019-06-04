---
title: ASPSP Sandbox
keywords: ASPSP Sandbox access
summary: "Details on the ASPSP Sandbox access for Open Banking testing"
sidebar: ob_sidebar
permalink: ob_sandbox.html
folder: prodOpenBanking
---


The ASPSP Sandbox allows you to simulate Open Banking calls by interacting with the **Nuapay Test Bank**. Depending on the integration mode, the method for accessing the test bank varies (see the following sections for details on the two modes):

## Self-Hosted Mode

For [Self-Hosted](ob_pispimplementation.html#self-hosted-mode) users who want to access the Test Bank:

1. Call the GET `/banks` service to retrieve the list of configured banks (see [Retrieve Banks](ob_getbank.html) for more information on this).
1. Note down the ID of the **Nuapay Test Bank**.
1. Call the POST `/payments` service (setting `integrationType` = `SELF_HOSTED` and providing the appropriate `bankId`, which you retrieved in step 2).
1. The response returns the `aspspAuthUrl` (the URL to the Sandbox ASPSP i.e. the Nuapay Test Bank)
1. Launch the returned URL in your browser and log on to the Nuapay Test Bank (ASPSP); use the following credentials: username = `psu` and password = `psu`


## Checkout Mode

For [Checkout](ob_pispimplementation.html#checkout-mode) users who want to access the Nuapay Test Bank:

1. Call the POST `/payments` service (setting `integrationType` = `CHECKOUT`).
1. On the Bank Selection screen that's rendered, select the **Nuapay Test Bank**.
1. Use the following credentials to log on: username = `psu` and password = `psu`


## Simulating Different Responses

When creating a payment, specify a differenet value for the pence amont to trigger specific transaction statuses as per the table below:

| **Payment Amount** | **Initial Status** | **Notes** | 
| Any Amount (not ending in .10 or .20) | SETTLEMENT_IN_PROGRESS | The payment is created as SETTLEMENT_IN_PROGRESS status; this status remains unchanged. |
| xxx.10 | SETTLEMENT_IN_PROGRESS | The payment is initially created as SETTLEMENT_IN_PROGRESS, once you call a GET `/payments/{paymentId}` for the transaction, the status will be returned as  SETTLEMENT_COMPLETE. This simulates the real-world scenario where it will typically take some time for the payment to update to its final status (generally in a matter of seconds).|
| xxx.20 |  SETTLEMENT_IN_PROGRESS | The payment is initially created as SETTLEMENT_IN_PROGRESS, once you call a GET `/payments/{paymentId}` for the transaction, the status will be returned as SETTLEMENT_REJECTED|


{% include links.html %}
