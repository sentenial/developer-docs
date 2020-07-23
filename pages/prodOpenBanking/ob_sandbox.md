---
title: ASPSP Sandbox
keywords: ASPSP Sandbox access
summary: "Details on the ASPSP Sandbox access for Open Banking testing"
sidebar: ob_sidebar
permalink: ob_sandbox.html
folder: prodOpenBanking
---


The ASPSP Sandbox allows you to simulate Open Banking calls by interacting with the **Nuapay Test Bank**. Depending on the integration mode, the method for accessing the test bank varies (see the following sections for details on the available modes):

## Checkout Mode

For [Checkout](ob_pispimplementation.html#checkout-mode) users who want to access the Nuapay Test Bank:

1. Call the POST `/payments` service (setting `integrationType` = `CHECKOUT`).
1. On the Bank Selection screen that's rendered, select the **Nuapay Test Bank**.
1. Use the following credentials to log on: username = `psu` and password = `psu`

## Self-Hosted Mode

For [Self-Hosted](ob_pispimplementation.html#self-hosted-mode) users who want to access the Test Bank:

1. Call the GET `/banks` service to retrieve the list of configured banks (see [Retrieve Banks](ob_getbank.html) for more information on this).
1. Note down the ID of the **Nuapay Test Bank**.
1. Call the POST `/payments` service (setting `integrationType` = `SELF_HOSTED` and providing the appropriate `bankId`, which you retrieved in step 2).
1. The response returns the `aspspAuthUrl` (the URL to the Sandbox ASPSP i.e. the Nuapay Test Bank)
1. Launch the returned URL in your browser and log on to the Nuapay Test Bank (ASPSP); use the following credentials: username = `psu` and password = `psu`


## Self-Hosted-Callback Mode

For [Self-Hosted-Callback](ob_pispimplementation.html#self-hosted-callback-mode) users who want to access the Test Bank:

1. Call the GET `/banks` service to retrieve the list of configured banks (see [Retrieve Banks](ob_getbank.html) for more information on this).
1. Note down the ID of the **Nuapay Test Bank**.
1. Call the POST `/payments` service (setting `integrationType` = `SELF_HOSTED_CALLBACK` and providing the appropriate `bankId`, which you retrieved in step 2).
1. The response returns the `aspspAuthUrl` (the URL to the Sandbox ASPSP i.e. the Nuapay Test Bank)
1. Launch the returned URL in your browser and log on to the Nuapay Test Bank (ASPSP); use the following credentials: username = `psu` and password = `psu`



## Simulating Different Responses

When creating a payment, specify a differenet value for the cents/pence amont to trigger a specific final transaction status:

| **Payment Amount** | **Final Status** | **Notes** | 
| Any Amount (not ending in .10, .20 or .30) | `SETTLEMENT_IN_PROGRESS` | After the payment is authorised by the PSU in the Nuapay Test Bank the payment status will transition to a final status of `SETTLEMENT_IN_PROGRESS`. |
| xxx.10 | `SETTLEMENT_COMPLETE` | After the payment is authorised by the PSU in the Nuapay Test Bank, the payment status will transition to a final status of `SETTLEMENT_COMPLETE`.  Once you call a **GET** `/payments/{paymentId}` ([Retrieve Payment](ob_retrievepayment.html)) for the transaction, the status will be returned as  `SETTLEMENT_COMPLETE`. This simulates the real-world scenario where it will typically take some time (generally only a few seconds) for the payment to update to its final status .|
| xxx.20 |  `SETTLEMENT_REJECTED` | After the payment is authorised by the PSU in the Nuapay Test Bank, the payment status will transition to a final status of `SETTLEMENT_REJECTED`. Call a **GET** `/payments/{paymentId}` ([Retrieve Payment](ob_retrievepayment.html)) for the transaction to confirm that its status is `SETTLEMENT_REJECTED`|
| xxx.30 | `PAYMENT_RECEIVED` | After the payment is authorised by the PSU in the Nuapay Test Bank, the payment status will transition initially to a status of `SETTLEMENT_COMPLETE`. Once you call a **GET** /payments/{paymentId} ([Retrieve Payment](ob_retrievepayment.html)) for the transaction, the status will be returned as `PAYMENT_RECEIVED`. This simulates the real-world scenario where it will typically take some time (typically a few seconds) for the payment to be credited to your Nuapay account.|

## Payment Transitions

The following table gives a summary of the status transitions, based on the amounts specified in the Test Bank:

<table>
  <tbody>
    <tr>
      <td><strong>Amount</strong></td>
      <td><strong>Statuses</strong></td>
    </tr>
    <tr>
      <td>Any Amount (not ending in .10, .20, .30)</td>
      <td>Status Transitions: 
      <ul>
      <li>PENDING</li> 
      <li>PENDING_APPROVAL</li> 
      <li>OAUTH_CALLBACK_COMPLETE</li>
      <li>AUTHORISED</li>
      <li><strong>SETTLEMENT_IN_PROGRESS</strong></li>
      </ul>
      </td>
    </tr>
    <tr>
      <td>Amount Ending in .10</td>
      <td>Status Transitions: 
      <ul>
      <li>PENDING</li> 
      <li>PENDING_APPROVAL</li> 
      <li>OAUTH_CALLBACK_COMPLETE</li>
      <li>AUTHORISED</li>
      <li><strong>SETTLEMENT_COMPLETE</strong></li>
      </ul>
      </td>
    </tr>
    <tr>
      <td>Amount Ending in .20</td>
      <td>Status Transitions: 
      <ul>
      <li>PENDING</li> 
      <li>PENDING_APPROVAL</li> 
      <li>OAUTH_CALLBACK_COMPLETE</li>
      <li>AUTHORISED</li>
      <li><strong>SETTLEMENT_REJECTED</strong></li>
      </ul>
      </td>
    </tr>
    <tr>
      <td>Amount Ending in .30</td>
      <td>Status Transitions: 
      <ul>
      <li>PENDING</li> 
      <li>PENDING_APPROVAL</li> 
      <li>OAUTH_CALLBACK_COMPLETE</li>
      <li>AUTHORISED</li>
      <li>SETTLEMENT_COMPLETE</li>
      <li><strong>PAYMENT_RECEIVED</strong></li>
      </ul>
      </td>
    </tr>
       </tbody>
       </table>

See [Payment Statuses](ob_paymentstatuses.html) For more information on the various possible statuses.

{% include links.html %}
