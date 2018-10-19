---
title: SEPA Reason Codes
keywords: SEPA Reason Codes SEPA Errors Instant CT Payments
summary: "SEPA Reason Codes - review the various SEPA Reason codes that are possible and how to best deal with them"
sidebar: ip_sidebar
permalink: ip_separeasons.html
folder: prodInstantPayments
toc: false
datatable: true
---

The following gives a list of the possible error codes that may be provided when a SEPA Instant Payment fails, as defined by the EBA Clearing, which may be useful when determining why a specific payment has been rejected:


## SEPA Reason Codes

The following is a summary of all possible SEPA R-transaction codes:


<div class="datatable-begin"></div>

 Code      | Description                                                                                            | 
---------- | -------------------------------------------------------------------------------------------------------| 
AB05       | Clearing process aborted due to timeout at the Beneficiary PSP (Creditor Agent).                       | 
AB06	   | Clearing process aborted due to timeout at Intermediary PSP or CSM (the Instructed Agent). Rejected by the CSM to Originator Bank upon Timeout condition|
AB07	   | Agent of message is not online / available. Generic usage if it cannot be determined who exactly is unavailable.|
AB08	   | Beneficiary PSP (Creditor Agent) is not online / available. |
AB09	   | Clearing process aborted due to error at the Beneficiary PSP (Creditor Agent).|
AB10	   | Clearing process aborted due to error at the Intermediary PSP or CSM (the Instructed Agent).|
AC01	   | Incorrect Account Number|
AC04	   | Closed Account Number |
AC06	   | Blocked Account |
AG01	   | Transaction Forbidden |
AG02	   | Invalid Bank Operation Code |
AG09	   | Original payment never received.|
AG10	   | Agent of message is suspended from the Real-time Payment system. Generic usage if it cannot be determined who exactly is suspended. |
AG11	   | Beneficiary PSP (Creditor Agent) of message is suspended from the Real-time Payment system.|
AM02	   | Not Allowed Amount|
AM04	   | Insufficient Funds| 
AM05	   | Duplication |
AM23	   | Transaction amount exceeds settlement limit|
ARDT	   | Already Returned Transaction| 
BE04	   | Missing Creditor Address|
CNOR	   | Creditor bank is not registered Beneficiary bank is not registered under this BIC in the CSM|
CUST	   | Requested By Customer |
DNOR	   | Debtor bank is not registered Originator bank is not registered under this BIC in the CSM |
DT01	   | Invalid Date |
DUPL	   | Duplicate Payment |
FOCR	   | Following Cancellation Request|
FRAD	   | Fraudulent Original SCT Inst Transaction |
LEGL	   | Legal Decision |
MD07	   | End Customer Deceased |
MS02	   | Not Specified Reason Customer Generated |
MS03	   | Not Specified Reason Agent Generated |
NOAS	   | No Answer from Customer |
NOOR	   | Original Credit Transfer never received |
PY01	   | Unknown BIC in routing table |
RC01	   | Bank Identifier Incorrect |
RR01	   | Missing Debtor Account Or Identification|
RR02	   | Missing Debtors Name Or Address |
RR03	   | Missing Creditors Name Or Address |
RR04	   | Regulatory Reason |
TECH	   | Technical Problem |
TM01	   | Invalid Cut Off Time Rejected by the CSM to Beneficiary Bank upon Timeout condition|
XD19	   | Invalid IBAN format| 
XT04	   | Insufficient liquidity for processing the transaction on the System.| 
XT06	   | Invalid AccptTime, Rejected by the CSM to Originator Bank upon exceeding tolerance period for the Acceptance Date&Time|
XT13	   | Unsupported XML field| 
XT33	   | Invalid data format |
XT73	   | Invalid country code |
XT75	   | Invalid original transaction status, action not required |
XT77	   | Original Amount mismatch |
XT79	   | The Debtor Agent is not allowed to send SCT Inst transactions (pacs.008) and consequently to send Investigation (pacs.028) and Recalls (camt.056). It is also not allowed to receive NRR and PRR. |
XT80	   | The Creditor Agent is not allowed to receive SCT Inst transactions (pacs.008) and consequently to receive Investigation (pacs.028) and Recalls (camt.056). It is also not allowed to send NRR and PRR.(The a admission profile “Debtor Only” currently is not implemented ) |
XT81	   | Field not Permitted in SCT Inst Service |
XT83	   | Participant not allowed to use the Product Id specified |
XT86	   | Expired Time limit for Recall |
XT87	   | Inconsistent Instructing Agent |
XT90	   | Invalid use of a Technical BIC |
            


<div class="datatable-end"></div>


{% include links.html %}
