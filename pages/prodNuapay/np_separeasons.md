---
title: SEPA Reason Codes
keywords: SEPA Reason Codes
summary: "SEPA Reason Codes - review the various SEPA Reason codes that are possible and how to best deal with them"
sidebar: np_sidebar
permalink: np_separeasons.html
folder: prodNuapay
toc: false
datatable: true
---

Direct Debit transactions can be unsuccessful for various reasons and when a payment fails, the original transaction's status is updated. 

The new status will generally be set to one of the following: 

* REJECTED
* REFUSED
* RETURNED
* REFUNDED 

(Collectively these statuses are often referred to as R-transactions). 

To help you to identify why the payment failed, error codes are provided by your payer's bank.

In this section we outline the various failed payments (R-transactions) and error codes that are possible, what they mean and what corrective action you should take based on the code.

{% include note.html content="The following guidance is based on the EPC recommendations (see the [EPC Web site] (https://www.europeanpaymentscouncil.eu/document-library/guidance-documents/guidance-reason-codes-sepa-direct-debit-r-transactions) for more details)." %}


{% include callout.html content="Certain error codes may be received both pre- and post-settlement.
Some banks may determine before the settlement date that your payer will have insufficient funds to make a payment; in this case you will receive a pre-settlement AM04 REJECT; other banks may wait until the actual settlement date to debit funds. If the funds are not available on the settlement date this would again result in an AM04 but in this scenario the R-transaction would be a post-settlement AM04 RETURN. In the table below the R-Transaction Type column indicates when the error code may be treated as a REJECT, CANCEL (pre-settlement) or a RETURN or a REFUND (post-settlement)." type="warning" %} 


## SEPA Reason Codes

The following is a summary of all possible SEPA R-transaction codes:


<div class="datatable-begin"></div>

 Code      | Description                                                                  |  Type              | Suggested Action
---------- | ---------------------------------------------------------------------------- | ------------------ | ----------------
AC01       | Format of the account number specified is not correct                        | REJECT  RETURN     | - Contact the Debtor in order to confirm the correctness of the Debtor’s IBAN<br/>- In case of mandate amendment: check the data provided by the Debtor<<br/>- Verify the database used for the BBAN conversion into IBAN.
AC04       | Account number specified has been closed                                     | REJECT   RETURN    | Contact the Debtor for the new account
AC06       | Account specified is blocked, prohibiting posting of transactions against it | REJECT   RETURN    | Contact the Debtor for alternative account/ solution to pay
AC13       | Invalid debtor account type                                                  | REJECT   RETURN    | - Contact the Debtor for clarification and to agree on another means of payment <br/>- Conclude the SDD Core mandate with Debtor
AG01       | Transaction forbidden on this type of account (formerly No Agreement)        | REJECT   RETURN    | Contact the Debtor in order to get information about the payment account to be used
AG02       | Bank Operation code specified in the message is not valid for receiver       | REJECT   RETURN    | - Contact your merchant bank to confirm what has caused this issue <br/> - Correct the wrong information
AM04       | Amount of funds available to cover specified message amount is insufficient  | REJECT   RETURN    | Contact the Debtor to ensure that there are funds on his account OR (Optionally) <a href= "np_representfaileddds.html">Re-present</a> the payment
AM05       | Duplication                                                                  | REJECT   RETURN    | Check if the collection is really duplicated
BE05       | Party who initiated the message is not recognised by the end customer        | REJECT   RETURN    | Creditor to contact the Creditor Bank
CNOR       | Creditor Bank is not registered under this BIC in the CSM                    | REJECT   RETURN    | Creditor to contact the Creditor Bank
CUST       | Cancellation of Credit Transfer payment, requested by the originator         | CANCEL             | 
CUTA       | Cancellation requested because an investigation request has been received and no remediation is possible. | CANCEL    | 
DNOR       | Debtor Bank is not registered under this BIC in the CSM                      | REJECT             | - Ask the Creditor Bank to check the reachability of the Debtor Bank <br/> - Contact Debtor to agree on another means of payment
DUPL       | Payment is a duplicate of another payment.                                   | CANCEL             | 
FF01       | 	File format incomplete or invalid                                         | REJECT   RETURN    | Contact Nuapay Support
MD01       | No mandate                                                                   | REJECT   RETURN  REFUND  | - Analyse the characteristics of the SEPA Direct Debit transaction <br/> - Contact the Debtor in the case of a refund
MD02       | Mandate related information data required by the scheme is missing           | REJECT             | Contact Nuapay Support
MD06       | Return of funds requested by end customer                                    | REFUND             | Contact the debtor
MD07       | End customer is deceased                                                     | REJECT   RETURN    | Close the agreement with deceased Debtor. See <a href = "np_cancelmandate.html">Cancel Mandate</a>
MS02       | Reason has not been specified by end customer                                | REJECT   RETURN    | Contact the Debtor
MS03       | Reason has not been specified by agent                                       | REJECT   RETURN    | Contact the Debtor 
RC01       | Bank Identifier code specified in the message has an incorrect format        | REJECT   RETURN    | Contact your bank
RR01       | Specification of the debtor's account or unique identification needed for reasons of regulatory requirements is insufficient or missing                                   | REJECT   RETURN    | Contact your bank
RR02       | Specification of the Debtor’s name and/or address needed for regulatory requirements is insufficient or missing | REJECT   RETURN    | Contact Nuapay Support
RR03       | Specification of the creditor’s name and/or address needed for regulatory requirements is insufficient or missing                                     | REJECT   RETURN     | Contact Nuapay Support
RR04       | Regulatory Reason                                                            | REJECT   RETURN    | Contact your bank
SL01       | Due to specific service offered by the Debtor Agent                          | REJECT   RETURN    | Contact your payer
UPAY       | Payment is not justified.                                                    | CANCEL             | 

<div class="datatable-end"></div>


{% include links.html %}
