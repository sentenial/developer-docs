---
title: Bacs Reason Codes
keywords: Bacs Reason Codes Errors
summary: "Bacs Codes - review the various Bascs Reason codes that are possible and how to best deal with them"
sidebar: np_sidebar
permalink: np_bacsreasons.html
folder: prodNuapay
toc: true
datatable: true
---

{% include note.html content="The following Reason Code listing is based on the latest Bacs Service User Guide. See the [Bacs Web site](https://www.bacs.co.uk/Pages/Home.aspx) for more details)." %}

## Unpaid Direct Debit Reason Codes

The following are the various reasons possible for Unpaid Bacs Direct Debits


<div class="datatable-begin"></div>

 Unpaid Code    | Reason                            |  Circumstances                | Special Instructions
----------------| ------------------------------    | ------------------            | ----------------
0               | Refer to payer                    | A payer’s bank is not in a position to pay the Direct Debit; (for some reason other than the exception below).OR The service of a Garnishee Order or Arrestment on the payer’s account, his bankruptcy, liquidation or appointment of receiver | Service user may represent up to one month from original processing day – it is recommended that the payer is notified of this 5 working days in advance of the representation. Service user will need to establish from the payer the reason for non-payment and likelihood of payment upon representation. 
1               | Instruction cancelled             | Instruction cancelled by payer or his bank | Service user must liaise with payer to agree the payment method for collection of any outstanding funds
2               | Payer deceased                    |                              | 
3               | Account transferred               | Account transferred to a new bank or building society | First check you have not been notified of the new bank details, if not you must obtain a new DDI from the payer. Collection must be suspended until a new DD set up and advance notice is issued to the payer
4               | Advance notice disputed           | Payer disputes time, amount or frequency of advance notice and has requested single payment to be countermanded | Service user should not collect further Direct Debits until it has resolved the dispute with the payer
5               | No account (OR wrong account type)| Account Number is not recognised at the paying bank | Service user should check DDI information and/or liaise with payer
6               | No Instruction                    | No Instruction held with paying bank | Service user should check DDI information and/or liaise with payer and if appropriate obtain new Instruction
7               | Amount differs                    | Payer states the amount of the Direct Debit differs from the amount in the advance notice to payer | Service user should not collect further Direct Debits until it has resolved the dispute with the payer
8               | Amount not yet due                | Payer states date of debiting is in advance of the due date specified in the advance notice to the payer. AUDDIS service users only – It is less than 2 working days since the DDI was lodged | Service user should not collect further Direct Debits until it has resolved the dispute with the payer
9               | Presentation overdue              | Payer states date of presentation is more than 3 working days after due date in advance notice to payer <br/><br/>OR<br/><br/> Re-presentation of Unpaid Direct Debit is more than one month from original Direct Debit processing day | Service user must give further advance notice to the payer before Direct Debit is collected
A               | Service user differs              | Identity of service user differs from DDI |
B               | Account closed                    | Payer has closed their account for an unknown reason | If the Direct Debit is to continue the service user must obtain a new DDI for a different/new account

<div class="datatable-end"></div>


## ADDACS Reason Codes

The following are possible codes Direct Debit Instruction Amendments and Cancellations:


<div class="datatable-begin"></div>

 Unpaid Code    | Reason                            |  Circumstances                | Special Instructions
----------------| ------------------------------    | ------------------            | ----------------
0               | Instruction cancelled - Refer to payer |Paying bank has cancelled Instruction | Service user cannot collect via Direct Debit on this account. If Direct Debit is to continue the service user must obtain a new DDI for a new account
1               | Instruction cancelled by payer    | Payer has instructed paying bank to cancel DDI| Service user must liaise with the payer to agree the payment method for collection of any outstanding debts
2               | Payer deceased                    |                              | 
3               | Account transferred to a new bank or building society            | Account transferred to a new bank or building society | If both old and new bank details are quoted you will need to amend your records accordingly. AUDDIS service users only – A 0N must be sent to lodge the new instruction. NB –With effect from 1 January 2013 do not send a 0C to the old bank to cancel the DDI. If only the old bank details are quoted first check you have been notified of new account details. If new account details have not been advised you must obtain a new DDI from the payer. Collection must be suspended until a new DDI set up and advance notice issued to the payer.
B               | Account closed                    | Payer has closed their account for an unknown reason | If the Direct Debit is to continue the service user must obtain a new DDI for a different/new account
C               | Account transferred to a different branch of bank/building society| New account details supplied to the service user | Service user must apply change to data file and continue with Direct Debit collections. AUDDIS service users only – A 0C/0N pair must not be sent on receipt of this message
D               | Advance notice disputed           | Payer disputes time, amount or frequency of advance notice | Service user should not collect further Direct Debits until it has resolved the dispute with the payer
E               | Instruction amended               | Paying bank will advise amendment via ADDACS message | Service user should collect Direct Debits using new details. AUDDIS service users only –A 0C/0N pair must not be sent on receipt of this message
R               | Instruction re-instated           | Paying bank may re-instate a cancelled DDI up to two months from cancelation | Service user may resume direct debiting under the reinstated Instruction. However, a new DDI must be obtained and lodged if re-instatement is identified after the two month period


<div class="datatable-end"></div>


## AUDDIS Reason Codes

The following are all possible codes related to the Automated Direct Debit Instruction Service​: 


<div class="datatable-begin"></div>

 Unpaid Code    | Reason                            |  Circumstances                | Special Instructions
----------------| ------------------------------    | ------------------            | ----------------
1               | Instruction cancelled             | Payer has instructed paying bank to cancel DDI | Service user must liaise with payer to agree the payment method for collection of any outstanding funds
2               | Payer deceased                    |                              | 
3               | Account transferred               | Account transferred to a new bank or building society | First check you have not been notified of the new bank details, if not you must obtain a new DDI from the payer. Collection must be suspended until a new DD set up and advance notice is issued to the payer
5               | No account                        | Account Number is not recognised at the paying bank | Service user should check DDI information and/or liaise with payer
6               | No Instruction                    | Instruction does not exist on paying bank’s database. (only applies to receipt of a 0C) | Service user should check DDI information and/or liaise with payer
7               | DDI amount not zero               | Validation has detected field 8 not zero or blank space filled | Service user should correct the record and resubmit
B               | Account closed                    | Payer has closed his account for an unknown reason| If the Direct Debit is to continue the service user must obtain a new DDI for a different/new account
C               | Account transferred to a different branch of the bank/building society| New account details supplied to the service user by paying bank | Service user should apply change to data file and continue with Direct Debit collections. A 0C/0N pair must not be sent on receipt of this message
F               | Invalid account type              | Paying bank does not allow Direct Debits on this type of account |Service user will need to obtain new account details from the payer. The Direct Debit cannot be applied
G               | Bank will not accept Direct Debits on account | Paying bank does not allow Direct Debits on this account | Service user must liaise with payer and obtain a new DDI for a different/new account
H               | Instruction has expired | Occurs when a service user attempts to convert a DDI which is shown as expired on the paying bank’s database| A 0N DDI will be required to re-activate this DDI if collections are to resume. Service users must ensure they have the payer’s authorisation to collect under expired Instruction
I               | Payer Reference is not unique | Paying bank has matched the DDI to an existing DDI with a similar reference that has more or fewer characters | Service user should allocate a different reference and lodge DDI, again using 0N
K               | Instruction cancelled by paying bank | Paying bank has cancelled the DDI | Service user cannot collect via Direct Debit on this account. If Direct Debit is to continue the service user must obtain a new DDI for a new account
L               | Incorrect payer’s Account Details | Possible issues: the sort code / account number has failed the modulus check; the sort code does not exist; the account number is not all numeric or is all zeros;the account type is invalid. | Service user should undertake sort code validation and modulus checking prior to sending the DDI transactions to the Bacs service or, if already doing this, should ensure that they are using the latest version
M               | Transaction Code / User Status incompatible | Transaction codes which are not allowed whilst in this status have been sent | Service user has sent ‘0S’ DDI transactions after being given ‘LIVE’ status on the Bacs service master files. Service user should re-submit transactions with 0N as the transaction code
N               | Transaction disallowed at payer’s branch | This code will be returned where paying banks have expressly disallowed the set-up of DDIs at the branch in field 1 of the transaction | Service user should refer back to their payer and obtain a DDI for a different/new account
O               | Invalid reference | The reference in field 10 of the DDI record does not comply with the AUDDIS rules | Service user should ensure that references meet the rules of the AUDDIS service (see Appendices section 12 of this document)
P               | Payer’s Name not present | Validation has detected field 11 is blank. A payer’s name should always be entered | Service user should correct the record and re-submit
Q               | Service user’s name blank | Validation has detected field 9 is blank. The service user’s company or trading name should always be entered | Service user should correct the record and re-submit


<div class="datatable-end"></div>


{% include note.html content="Reason codes 7 and L to Q are only generated by the Bacs service and occur as a result of its validation of DDI records" %}





{% include links.html %}
