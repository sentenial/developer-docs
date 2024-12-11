---
title: Bacs Reason Codes
keywords: Bacs Reason Codes Errors
summary: "Bacs Codes - review the various Bascs Reason codes that are possible and how to best deal with them"
sidebar: resources_sidebar
permalink: np_bacsreasons.html
folder: prodNuapay
toc: true
datatable: true
---

## ARUDD Reason Codes

The following are the Automated Return of Unpaid Direct Debit (ARUDD) reason codes:


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

The following are the Automated Direct Debit Amendment and Cancellation Service (ADDACS) reason codes:


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

The following are all possible codes related to the Automated Direct Debit Instruction Service​ (AUDDIS):


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



## DDIC Reason Codes

{% include tip.html content="For full details on Direct Debit Indemnity Claims (DDICs), please refer to the official Bacs Service User Guide, available from [https://www.bacs.co.uk/sugr/pages/sugrdd.aspx](https://www.bacs.co.uk/sugr/pages/sugrdd.aspx){:target='_blank'}" %}

The following are all possible codes related to DDICs. In addition, valid reasons for challenging an indemnity claim are provided below. These have been taken from the Bacs Service User Guide and are intended for reference purposes only. Please refer to the Bacs Service User Guide for full details and background information:

<div class="datatable-begin"></div>

 Reason Code    | Reason                            |  Circumstances                | Challenge Reasons
----------------| ------------------------------    | ------------------            | ----------------
1               | Amount and / or date of Direct Debit differ from Advance Notice   | | Where the service user can produce either a copy of the advance notice or a copy of a contract signed by the payer detailing the amounts to be collected and the collection dates. |
2               | No advanced notice received by payer.| Payer did not receive pre-notification of the debit. | Where the service user can produce either a copy of a contract signed by the payer which includes the advance notice, or an email / text sent to the payer which includes the advance notice.
3               | DDI cancelled by paying bank.              | | Where the paying PSP fails to send a cancellation advice to the service user on or before the date the debit was presented against the payer’s account. Or in the case of a paper indemnity claim, the paying PSP fails to include the date of cancellation within the form
4               | Payer has cancelled DDI directly with Service User |  | None.
5               | **AUDDIS service users only** - No Instruction held. | Payer disputes giving authority.  | **AUDDIS** service users may provide one or more of the following as evidence: <br /><br />(1) A valid instruction e.g. one retained by the service user in accordance with the AUDDIS requirements. <br />(2) Evidence of a contract signed by the payer that specifically references payment by Direct Debit. <br />(3) Evidence of a contract that specifically references payment by Direct Debit – this need not be signed by the payer where the payer does not dispute the existence of the contract, merely the payment method. <br />(4) Evidence showing that the payer has confirmed receipt of a nominal amount into their account by provision of an associated reference to the service user <br />(5) Results evidencing the completion of the payer verification measures, previously agreed as acceptable between the service user and their sponsor. <br /><br />**Non-AUDDIS** service users may raise a challenge where: <br /><br />(1) the paying PSP has directed a claim for reason code 5 against a non-AUDDIS service user<br /> (2) the paying PSP has returned a Direct Debit with a 01 transaction code ‘refer to payer’ and has subsequently raised an indemnity claim for the reason ‘payer disputes having given authority’ in respect of a representation with an 18 transaction code.
6               | **AUDDIS service users only** - signature on DDI is fraudulent or not in accordance with account authorised signature(s).|  | **AUDDIS service users** - where no request has previously been received from the paying PSP to provide a copy of the DDI <br /> **Non-AUDDIS service users** - where a claim is received by a Non-AUDDIS service user
7               | Claim raised at Service User's request after Direct Debit applied to payer's account. | The request will not be accepted by the paying PSP until after payment has been debited to the payer’s account. No action will be taken on any request until it has been confirmed in writing to the paying PSP e.g. by fax / email. Details of the confirmation will be submitted with the indemnity claim. | Where the indemnity claim for reason code 7 (indemnity claim raised at service user’s request) is disputed. The paying PSP is required to uphold the challenge if the fax / email provided by the service user cannot be produced.
8               | Service User Name disputed | Payer does not recognise the Service User collecting Direct Debit.| **AUDDIS service users** – may provide one or more of the following as evidence: <br /><br /> (1) A valid instruction e.g. one retained by the service user in accordance with the AUDDIS requirements <br />(2) A contract signed by the payer that specifically references payment by Direct Debit <br />(3) A contract that specifically references payment by Direct Debit – this need not be signed by the payer where the payer does not dispute the existence of the contract, merely the payment method <br />(4) Evidence showing that the payer has confirmed receipt of a nominal amount into their account by provision of an associated reference to the service user <br />(5) Correspondence addressed to the payer relating to the Direct Debit e.g. advance notice, from a service user with the same name as on the Direct Debit collection <br />(6) Results evidencing the completion of the payer verification measures (as required under section 3C of this Guide & Rules), previously agreed as acceptable between the service user and their sponsor.

<div class="datatable-end"></div>

## ARUCS Reason Codes

The following are the Automated Return of Unapplied Credits (ARUCS) reason codes:


<div class="datatable-begin"></div>

Code | Reason                      | Circumstances                                             | Special Instructions
-----|-----------------------------|----------------------------------------------------------|---------------------
0    | Invalid details             | The account details were not recognized.                | The service user should contact the beneficiary for new details.
2    | Beneficiary deceased        | The beneficiary of the credit has died.                 |
3    | Account transferred         | The beneficiary's account has been transferred to another bank or building society. | The service user should contact the beneficiary for the new account details.
5    | No account                  | There is no account matching the details provided.       | The service user should check the details and/or contact the beneficiary.
B    | Account closed              | The beneficiary's account has been closed.              | The service user should contact the beneficiary for new account details.
C    | Requested by originator     | The originator of the credit has requested the payment not be applied. | The service user should contact the originator of the credit for instructions.



<div class="datatable-end"></div>






{% include links.html %}
