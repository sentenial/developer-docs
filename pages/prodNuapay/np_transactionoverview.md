---
title: Transaction Overview
keywords: Transaction Overview
summary: "Various transaction types are stored on your Nuapay account. This section gives a breakdown of the possible types"
sidebar: acc_sidebar
permalink: np_transactionoverview.html
folder: prodNuapay
---

The following transactions may be recorded on your Nuapay account:


Our API allows you to carry out various operations on your account:


<table>
<thead>
<tr>
<th>Transaction</th>
<th>Transaction Type</th>
<th>Debit Credit Indicator</th>
<th>Counterparty  </th>
</tr>
</thead>
<tbody>
<tr>
<td>Direct Debit Batch</td>
<td><code>DIRECT_DEBIT_BATCH</code></td>
<td><code>CREDIT</code></td>
<td>Creditor</td>
</tr>
<tr>
<td>Direct Debit Bank Cancellation</td>
<td><code>DIRECT_DEBIT_BANK_CANCELLATION</code></td>
<td><code>DEBIT</code></td>
<td>Creditor</td>
</tr>
<tr>
<td>Direct Debit Reject</td>
<td><code>DIRECT_DEBIT_REJECT</code></td>
<td><code>DEBIT</code></td>
<td>Creditor</td>
</tr>
<tr>
<td>Direct Debit Reversal</td>
<td><code>DIRECT_DEBIT_REVERSAL</code></td>
<td><code>DEBIT</code></td>
<td>Creditor</td>
</tr>
<tr>
<td>Direct Debit Return</td>
<td><code>DIRECT_DEBIT_RETURN</code></td>
<td><code>DEBIT</code></td>
<td>Creditor</td>
</tr>
<tr>
<td>Direct Debit Refusal</td>
<td><code>DIRECT_DEBIT_REFUSAL</code></td>
<td><code>DEBIT</code></td>
<td>Creditor</td>
</tr>
<tr>
<td>Direct Debit Authorized Refund</td>
<td><code>DIRECT_DEBIT_AUTHORIZED_REFUND</code></td>
<td><code>DEBIT</code></td>
<td>Creditor</td>
</tr>
<tr>
<td>Direct Debit Unauthorized Refund</td>
<td><code>DIRECT_DEBIT_UNAUTHORIZED_REFUND</code></td>
<td><code>DEBIT</code></td>
<td>Creditor</td>
</tr>
<tr>
<td>Direct Debit Batch Transactions Fee</td>
<td><code>DIRECT_DEBIT_BATCH_TRANSACTIONS_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>Direct Debit R-Transaction Fee</td>
<td><code>DIRECT_DEBIT_RTRANSACTIONS_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>Credit Transfer Bank Reject</td>
<td><code>CREDIT_TRANSFER_BANK_REJECT</code></td>
<td><code>CREDIT</code></td>
<td>Debtor</td>
</tr>
<tr>
<td>Outgoing Credit Transfer</td>
<td><code>OUTGOING_CREDIT_TRANSFER</code></td>
<td><code>DEBIT</code></td>
<td>Creditor</td>
</tr>
<tr>
<td>Credit Transfer Reject Fee</td>
<td><code>CREDIT_TRANSFER_RTRANSACTION_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>Incoming Credit Transfer</td>
<td><code>INCOMING_CREDIT_TRANSFER</code></td>
<td><code>CREDIT</code></td>
<td>Debtor</td>
</tr>
<tr>
<td>Credit Transfer Recall</td>
<td><code>CREDIT_TRANSFER_RECALL</code></td>
<td><code>CREDIT</code></td>
<td>Debtor</td>
</tr>

<tr>
<td>Credit Transfer Batch</td>
<td><code>CREDIT_TRANSFER_BATCH</code></td>
<td><code>DEBIT</code></td>
<td>Creditor</td>
</tr>

<tr>
<td>Credit Transfer Technical Reject</td>
<td><code>CREDIT_TRANSFER_TECH_REJECT</code></td>
<td><code>CREDIT</code></td>
<td>Debtor</td>
</tr>

<tr>
<td>Instant Credit Transfer</td>
<td><code>INCOMING_INSTANT_CREDIT_TRANSFER</code></td>
<td><code>CREDIT</code></td>
<td>Debtor</td>
</tr>
<tr>
<td>Incoming Faster Payment</td>
<td><code>INCOMING_FPM_CREDIT_TRANSFER</code></td>
<td><code>CREDIT</code></td>
<td>Debtor</td>
</tr>
<tr>
<td>Availability Fee</td>
<td><code>AVAILABILITY_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>Outgoing Credit Transfer Fee</td>
<td><code>OUTGOING_CREDIT_TRANSFER_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>Incoming Credit Transfer Fee</td>
<td><code>INCOMING_CREDIT_TRANSFER_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>Credit Transfer Recall Fee</td>
<td><code>CREDIT_TRANSFER_RECALL_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>E-Mandate Setup Fee - CORE Scheme</td>
<td><code>CORE_EMANDATE_SETUP_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>E-Mandate Setup Fee - BACS Scheme</td>
<td><code>BACS_EMANDATE_SETUP_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>E-Mandate Setup Fee - B2B Scheme</td>
<td><code>B2B_EMANDATE_SETUP_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>E-Mandate Fee - CORE Scheme</td>
<td><code>CORE_EMANDATE_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>E-Mandate Fee - BACS Scheme</td>
<td><code>BACS_EMANDATE_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>E-Mandate Fee - B2B Scheme</td>
<td><code>B2B_EMANDATE_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>Overdraft Fee</td>
<td><code>OVERDRAFT_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>Credit Adjustment</td>
<td><code>CUSTOMER_ADJUSTMENT_CREDIT</code></td>
<td><code>CREDIT</code></td>
<td>N/A Nuapay adjustment</td>
</tr>
<tr>
<td>Debit Adjustment</td>
<td><code>CUSTOMER_ADJUSTMENT_DEBIT</code></td>
<td><code>DEBIT</code></td>
<td>N/A Nuapay adjustment</td>
</tr>
<tr>
<td>Bacs File Export Fee</td>
<td><code>BACS_DIRECT_DEBIT_FILE_EXPORT_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>Bacs Mandate File Export Fee</td>
<td><code>BACS_MANDATE_FILE_EXPORT_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>SEPA File Export Fee</td>
<td><code>SEPA_DIRECT_DEBIT_FILE_EXPORT_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>R-Transaction Fee</td>
<td><code>DIRECT_DEBIT_RTRANSACTION_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>Transfer Between Nuapay Accounts</td>
<td><code>OWN_ACCOUNT_DEBIT_TRANSFER</code></td>
<td><code>DEBIT</code></td>
<td>N/A Account Transfer</td>
</tr>
<tr>
<td>Transfer Between Nuapay Accounts</td>
<td><code>OWN_ACCOUNT_CREDIT_TRANSFER</code></td>
<td><code>CREDIT</code></td>
<td>N/A Account Transfer</td>
</tr>
<tr>
<td>Ad Hoc Fee</td>
<td><code>OCX_ADHOC_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>CT Reject Fee</td>
<td><code>CREDIT_TRANSFER_REJECT_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>Express CT Reject Fee</td>
<td><code>REJECTED_EXPRESS_CREDIT_TRANSFER_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>Incoming Express CT Fee</td>
<td><code>INCOMING_EXPRESS_CREDIT_TRANSFER_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
<tr>
<td>Instant CT Outgoing</td>
<td><code>INSTANT_CREDIT_TRANSFER_OUT</code></td>
<td><code>DEBIT</code></td>
<td>Creditor</td>
</tr>
<tr>
<td>Outgoing Faster Payment</td>
<td><code>OUTGOING_FPS_CREDIT_TRANSFER</code></td>
<td><code>DEBIT</code></td>
<td>Creditor</td>
</tr>
<tr>
<td>Outgoing Express CT Fee</td>
<td><code>OUTGOING_EXPRESS_CREDIT_TRANSFER_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
</tbody>
</table>



{% include links.html %}
