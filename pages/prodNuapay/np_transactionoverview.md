---
title: Transaction Overview
keywords: Transaction Overview
summary: "Various transaction types are stored on your Nuapay account. This section gives a breakdown of the possible types"
sidebar: np_sidebar
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
<td>Credit Transfer Bank Reject</td>
<td><code>CREDIT_TRANSFER_BANK_REJECT</code></td>
<td><code>CREDIT</code></td>
<td>Debtor</td>
</tr>
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
<td><code>DIRECT_DEBIT_AUTHORIZED_REFUND</code></td>
<td><code>DEBIT</code></td>
<td>Creditor</td>
</tr>
<tr>
<td>Outgoing Credit Transfer</td>
<td><code>OUTGOING_CREDIT_TRANSFER</code></td>
<td><code>DEBIT</code></td>
<td>Creditor</td>
</tr>
<tr>
<td>Availability Fee</td>
<td><code>AVAILABILITY_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
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
<td>Overdraft Fee</td>
<td><code>OVERDRAFT_FEE</code></td>
<td><code>DEBIT</code></td>
<td>N/A for Fees</td>
</tr>
</tbody>
</table>



{% include links.html %}
