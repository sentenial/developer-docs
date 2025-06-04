---
title: Ledger Accounts Overview
keywords: Ledger Accounts Overview
summary: "Ledger Accounts allow you to manage postings internally via internal accounts. This page offers a guide to how ledger accounts can be structured and used. "
sidebar: acc_sidebar
permalink: np_ledgeraccsoverview.html
folder: prodNuapay
---

Nuapay's Ledger Solution offers **Ledger Accounts** for customers or operational categories and groups them into **Ledger Collective Accounts** for reporting and control. 
* This structure supports use cases like Pay-As-You-Go (PAYG) services, where internal account management and pre-funding are required.
* This page walks through a **sample ledger configuration and fund flow**, explaining how internal ledger movements interact with your real bank account, and how customer and operational transactions are tracked, matched, and reconciled.


{% include tip.html content="The following example is **just one of many possible configurations**. Your actual setup may vary depending on your product design and financial operations model." %}

## Overview of a Sample Flow

The following details how funds flow between internal ledger accounts (customer, revenue, control, and error accounts), and how entries reflect in the real bank account.

Note that the ledger system:
* Supports **double-entry accounting**, ensuring all debits equal credits. 
* Operates with **collective accounts** for grouped logic and **individual ledger accounts** per customer or operational category.
* Assumes that the merchant's customers have been instructed to provide a unique reference when issuing credits so that their payments can be posted to their unique Ledger Account.

## Entities and Account Types

Assume that we have enabled the Ledger Accounts product and have the following account setup:

<img src = 'images/led_acc_hierarchy.png'>

### 1. Merchant Real (Nuapay) Account 

- A real bank account holding actual funds.

### 2. Collective Accounts

Used for grouping related ledger accounts:

#### a. CustomerLedgerCollectiveAccount1

- Customer1Ledger (CUST1L1)
- Customer2Ledger (CUST1L2)

#### b. OperationLedgerCollectiveAccount2

- Customer Funds Control
- Revenue Account
- Error Account

## Incoming Payment Flow

### Step 1: Incoming Payment Registered

A payment is received into the Nuapay account:

| Account               | Change |
|-----------------------|--------|
| Real Account          | +100   |
| Nuapay Internal       | -100   |

{% include tip.html content="The Nuapay Internal Account holds the contra booking to the credit on the merchant's real account: the merchant has no access to this account." %}


### Step 2: Webhook Trigger

Once the credit is processed on the real account: 
* An [Account Entry](np_whacccentry.html) Webhook is dispatched to notify the merchant of the payment.
* The Webook includes the `resourceRemittanceInformation`, which is the reference to the customer's Ledger Account (*CUST1L1*).
* The merchant must apply the credit posting to the appropriate Ledger Account via the `POST /ledgeraccounts/transfers` service.
* The contra debit posting is made against the *Customer Funds Control* account.


```http
POST /ledgeraccounts/transfers
{
  "accountFrom": "Customer Funds Control",
  "accountTo": "CUST1L1",
  "valueDate": "2025-11-01",
  "amount": 100.00,
  "remittanceInfo": "Topup payment CUST1L1-NOV25",
  "category": "CUSTOMER_TOP_UP"
}
```

Following that transfer the Ledger entries are updated and the funds are held as follows:


| Account                     | Change |
|-----------------------------|--------|
| Customer Funds Control      | -100   |
| Customer1Ledger (CUST1L1)   | +100   |

{% include note.html content="Funds are always held on the Real Account. Ledger Accounts are a way to logically assign those funds to nominal Ledger Accounts: funds are not actually credited or debited between these accounts." %}

### Step 3: Handling a Second Payment – To Another Ledger

Where a second payment is processed, this time for CUST1L2, the following request is generated.
Note that:
* `CUST1L2` is credited.
* The `accountFrom` (the *Customer Funds Control*) is updated with the contra booking.

```http
POST /ledgeraccounts/transfers
{
  "accountFrom": "Customer Funds Control",
  "accountTo": "CUST1L2",
  "valueDate": "2025-11-01",
  "amount": 100.00,
  "remittanceInfo": "Topup payment CUST1L2-NOV25",
  "category": "CUSTOMER_TOP_UP"
}
```

Ledger entries:

| Account                     | Change |
|-----------------------------|--------|
| Customer Funds Control      | -100   |
| Customer2Ledger (CUST1L2)   | +100   |

**Cumulative**:

| Account                     | Balance |
|-----------------------------|---------|
| Customer Funds Control      | -200    |
| CUST1L1                     | +100    |
| CUST1L2                     | +100    |
| Real Account                | +200    |
| Nuapay Internal             | -200    |

### Step 4: Unmatched Reference → Route to Error Account

Where a third payment is received but the reference provided cannot be matched to an appropriate Ledger Account, that payment would must be posted to the Error Account:

```http
POST /ledgeraccounts/transfers
{
  "accountFrom": "Customer Funds Control",
  "accountTo": "Error Account",
  "valueDate": "2025-11-01",
  "amount": 100.00,
  "remittanceInfo": "Topup payment COOST1L2-DEC25",
  "category": "CUSTOMER_TOP_UP"
}
```
Ledger entries:

| Account                     | Change |
|-----------------------------|--------|
| Customer Funds Control      | -100   |
| Error Account               | +100   |

**Cumulative**:

| Customer Funds Control      | -300   |
| Customer1Ledger (CUST1L1)   | +100   |
| Customer2Ledger (CUST1L2)   | +100   |
| Error Account               | +100   |
| Real Account                | +300   |
| Nuapay Internal             | -300   |

Note that the Ledger Accounts are grouped under two distinct Ledger Collective Accounts so it is possible to visualise the accounts as follows:

<img src='images/led_overview.png'>



## Manual Correction (Reconciliation)

Any payments that are unmatched and posted to the Error Account will need to be reviewed. In the example above, the following reference was provided:

`Topup payment COOST1L2-DEC25`

When this is reviewed, the user decides that this was a payment intended for `CUST1L2` so a transfer is made to move the posting from the Error Account to the correct Ledger Account:

```http
POST /ledgeraccounts/transfers
{
  "accountFrom": "Error Account",
  "accountTo": "CUST1L2",
  "valueDate": "2025-11-01",
  "amount": 100.00,
  "remittanceInfo": "Topup payment CUST1L2-DEC25",
  "category": "CUSTOMER_TOP_UP"
}
```

Ledger entries following this transfer:

| Account                     | Change |
|-----------------------------|--------|
| Error Account               | -100   |
| Customer2Ledger (CUST1L2)   | +100   |

**Cumulative**:

| Customer Funds Control      | -300   |
| CUST1L1                     | +100   |
| CUST1L2                     | +200   |
| Error Account               | 0      |

## Revenue Booking

In order to post revenue to an external account, funds are moved from the customer ledgers to a revenue account. In this example, assume that 80.00 is to be transferred from both customer Ledger Accounts:

```http
POST /ledgeraccounts/transfers
{
  "accountFrom": "CUST1L1",
  "accountTo": "Revenue Account",
  "valueDate": "2025-11-05",
  "amount": 80.00,
  "remittanceInfo": "Move to Revenue",
  "category": "REVENUE"
}
```

And

```http
POST /ledgeraccounts/transfers
{
  "accountFrom": "CUST1L2",
  "accountTo": "Revenue Account",
  "valueDate": "2025-11-05",
  "amount": 80.00,
  "remittanceInfo": "Move to Revenue",
  "category": "REVENUE"
}
```

Ledger entries:

| Account                     | Change |
|-----------------------------|--------|
| Customer1Ledger (CUST1L1)   | -80    |
| Customer2Ledger (CUST1L2)   | -80    |
| Revenue Account             | +160   |

**Cumulative**:

| CUST1L1                     | +20    |
| CUST1L2                     | +120   |
| Revenue Account             | +160   |


## Payout / Settlement

### Step 1: Move Funds from Ledger to Control

Call the service to move funds from the *Revenue Account* to the *Customer Funds Control* account:

```http
POST /ledgeraccounts/transfers
{
  "accountFrom": "Revenue Account",
  "accountTo": "Customer Funds Control",
  "valueDate": "2025-11-05",
  "amount": 160.00,
  "remittanceInfo": "Move to Control",
  "category": "REVENUE"
}
```

### Step 2: Real Bank Transaction

To trigger the transfer from the Real Nuapay Account to the merchant's High-Street account, use the [Create CT](np_createct.html) endpoint.

Transfer from Revenue to Control

| Revenue Account             | -160   |
| Customer Funds Control      | +160   |

Bank payout to merchant

| Real Account                | -160   |
| Nuapay Internal             | +160   |

## Summary of Ledger Entries

Following the outgoing Credit Transfer, the following balances are stored on the various Real and Ledger Collective and Ledger accounts:

| Account                          | Balance |
|----------------------------------|---------|
| Real Account                     | +140    |
| CustomerLedgerCollectiveAccount1| +140    |
|   └─ CUST1L1                     | +20     |
|   └─ CUST1L2                     | +120    |
| Customer Funds Control           | +140    |
| Revenue Account                  | 0       |
| Error Account                    | 0       |
