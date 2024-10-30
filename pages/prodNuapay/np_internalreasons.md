---
title: SEPA Reason Codes
keywords: SEPA Reason Codes SEPA Errors
summary: "SEPA Reason Codes - review the various SEPA Reason codes that are possible and how to best deal with them"
sidebar: resources_sidebar
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

{% include note.html content="The following guidance is based on the EPC recommendations (see the [EPC Web site](https://www.europeanpaymentscouncil.eu/document-library/guidance-documents/guidance-reason-codes-sepa-direct-debit-r-transactions) for more details)." %}


{% include callout.html content="Certain error codes may be received both pre- and post-settlement.
Some banks may determine before the settlement date that your payer will have insufficient funds to make a payment; in this case you will receive a pre-settlement AM04 REJECT; other banks may wait until the actual settlement date to debit funds. If the funds are not available on the settlement date this would again result in an AM04 but in this scenario the R-transaction would be a post-settlement AM04 RETURN. In the table below the R-Transaction Type column indicates when the error code may be treated as a REJECT, CANCEL (pre-settlement) or a RETURN or a REFUND (post-settlement)." type="warning" %}


## SEPA Reason Codes

The following is a summary of all possible SEPA R-transaction codes:


<div class="datatable-begin"></div>

 Code      | Description                                                                  |  Type              | Suggested Action
---------- | ---------------------------------------------------------------------------- | ------------------ | ----------------
AC01       | Format of the account number specified is not correct                        | REJECT  RETURN     | - Contact the Debtor in order to confirm the correctness of the Debtor’s IBAN <br/>- In case of mandate amendment: check the data provided by the Debtor <br/>- Verify the database used for the BBAN conversion into IBAN.
AC04       | Account number specified has been closed. In some countries, MS03 may be used in this scenario (due to data protection regulations).                                     | REJECT   RETURN    | Contact the Debtor for the new account
AC06       | Account specified is blocked, prohibiting posting of transactions against it | REJECT   RETURN    | Contact the Debtor for alternative account/ solution to pay
AC13       | Invalid debtor account type                                                  | REJECT   RETURN    | - Contact the Debtor for clarification and to agree on another means of payment <br/>- Conclude the SDD Core mandate with Debtor
AG01       | Transaction forbidden on this type of account (formerly No Agreement)        | REJECT   RETURN    | Contact the Debtor in order to get information about the payment account to be used
AG02       | Bank Operation code specified in the message is not valid for receiver       | REJECT   RETURN    | - Contact your merchant bank to confirm what has caused this issue <br/> - Correct the wrong information
AM04       | Amount of funds available to cover specified message amount is insufficient  | REJECT   RETURN    | Contact the Debtor to ensure that there are funds on his account OR (Optionally) <a href= "np_representfaileddds.html">Re-present</a> the payment
AM05       | Duplication                                                                  | REJECT   RETURN  REVERSAL  | Check if the collection is really duplicated
BE05       | Party who initiated the message is not recognised by the end customer        | REJECT   RETURN    | Creditor to contact the Creditor Bank
CNOR       | Creditor Bank is not registered under this BIC in the CSM                    | REJECT       | Creditor to contact the Creditor Bank
CUST       | Cancellation of Credit Transfer payment, requested by the originator         | CANCEL             |
CUTA       | Cancellation requested because an investigation request has been received and no remediation is possible. | CANCEL    |
DNOR       | Debtor Bank is not registered under this BIC in the CSM                      | REJECT       | - Ask the Creditor Bank to check the reachability of the Debtor Bank <br/> - Contact Debtor to agree on another means of payment
DUPL       | Payment is a duplicate of another payment.                                   | CANCEL             |
ED05       | Settlement failed                                                          | REJECT               | Contact the debtor
FF01       | 	File format incomplete or invalid                                         | REJECT   | Contact Nuapay Support
MD01       | No mandate. **CORE SDD**: no valid mandate; **B2B SDD**: no valid mandate or unable to determine if the debtor has lodged a mandate; or unathorised transaction (for refunds of SDD CORE collections). -                                                                  | REJECT   RETURN  REFUND  | - Analyse the characteristics of the SEPA Direct Debit transaction <br/> - Contact the Debtor in the case of a refund
MD02       | Mandate related information data required by the scheme is missing           | REJECT             | Contact Nuapay Support
MD06       | Return of funds requested by end customer                                    | REFUND             | Contact the debtor
MD07       | End customer is deceased. In some countries, MS03 may be used in this scenario (due to data protection regulations).                                                    | REJECT   RETURN    | Close the agreement with deceased Debtor. See <a href = "np_cancelmandate.html">Cancel Mandate</a>
MS02       | Reason has not been specified by end customer                                | REJECT   RETURN   REVERSAL REFUSAL  | Contact the Debtor
MS03       | Reason has not been specified by agent. Banks should only use this code where national legislation (e.g. data protection laws) does not allow for the use of AC04, AM04, MD07, RR01, RR02, RR03, and RR04.                                       | REJECT   RETURN  REVERSAL   | Contact the Debtor
RC01       | Bank Identifier code specified in the message has an incorrect format        | REJECT   RETURN    | Contact your bank
RR01       | Specification of the debtor's account or unique identification needed for reasons of regulatory requirements is insufficient or missing                                   | REJECT   RETURN    | Contact your bank
RR02       | Specification of the Debtor’s name and/or address needed for regulatory requirements is insufficient or missing. In some countries, MS03 may be used in this scenario (due to data protection regulations). | REJECT   RETURN    | Contact Nuapay Support
RR03       | Specification of the creditor’s name and/or address needed for regulatory requirements is insufficient or missing. In some countries, MS03 may be used in this scenario (due to data protection regulations).                                     | REJECT   RETURN     | Contact Nuapay Support
RR04       | Regulatory Reason - used where RR01, RR02 or RR03 are not applicable. In some countries, MS03 may be used in this scenario (due to data protection regulations)                                                          | REJECT   RETURN    | Contact your bank
SL01       | Due to specific service offered by the Debtor Agent                          | REJECT   RETURN    | Contact your payer
UPAY       | Payment is not justified.                                                    | CANCEL             |

<div class="datatable-end"></div>

### Application Error codes

<div class="datatable-begin"></div>

Code       | Description                                                                  
---------- | ----------------------------------------------------------------------------
CT001	   | Enter valid Execution Date
CT002	   | Execution Date is in the past
CT003	   | Execution Date is today and cut-off time has passed. Please select future date.
CT004	   | Invalid Payment Amount
CT005	   | Invalid character in Payment Reference
CT006	   | Payment Reference is too long
CT007	   | Invalid character in Remittance Info
CT008	   | Remittance Info is too long
CT009	   | Payment reference already exists for Originator
CT010	   | Beneficiary Bank Branch is not compliant for SEPA Credit Transfers
CT011	   | Originator Account provided does not exist within the Originator setup targeted, or is not in a valid status
CT012	   | Beneficiary Account Details are invalid
CT013	   | Total Number of Transactions in the File does not match the File Check Sum
CT014	   | Sum of all CT Amounts in the File does not match the File Check Sum
CT015	   | Total Number of Transactions in the Batch does not match the Batch Check Sum
CT016	   | Sum of CT all Amounts in the Batch does not match the Batch Check Sum
CT017	   | Invalid character in Payment Reference
CT018	   | Beneficiary Account Country field is Required when Beneficiary Domestic Account Details are provided
CT019	   | Beneficiary Country must be provided when a Beneficiary Address Related field has been provided
CT020	   | Beneficiary phone number is not well formed
CT021	   | Beneficiary mobile number is not well formed
CT022	   | Beneficiary email address format is invalid
CT023	   | CT's Beneficiary does not exist within the Target Originator Setup
CT024	   | Unstructured remittance Information exceeds 140 characters
CT025	   | Beneficiary email address length is invalid
CT026	   | Beneficiary phone number length is invalid
CT027	   | Beneficiary mobile number length is invalid
CT028	   | Beneficiary address state/province length is invalid
CT029	   | Beneficiary address town length is invalid
CT030	   | Beneficiary address post code length is invalid
CT031	   | Beneficiary address country length is invalid
CT032	   | Beneficiary address line 1 length is invalid
CT033	   | Beneficiary address line 2 length is invalid
CT034	   | Description of purpose length is invalid
CT035	   | Beneficiary name is required
CT036	   | Beneficiary name length is invalid
CT037	   | Beneficiary IBAN should be unique per originator
CT038	   | Duplicate File or Invalid File Reference
CT039	   | Credit Transfer amount must be provided
CT040	   | Transfer Failed. Please try again later
CT041	   | Transfer Failed. Please contact support
CT042	   | Insufficient Funds
CT043	   | Creditor Bank BIC is required as Creditor Bank is located in a NON-EEA Country
CT044	   | Originator account currency does not match payment currency
CT045	   | Payment amount exceeds max allowed scheme limit
CT046	   | Requested payment type is not supported by Originator
CT047	   | The Execution Date must be set to today's date.
CT048	   | Payment Type is not allowed for current Originator configuration. Please contact support.
CT049	   | Remittance Information invalid.
CT050	   | End to End ID invalid, it must follow GBP EXPRESS UK FASTER PAYMENTS payments rules.
CT051	   | Beneficiary Account is not reachable for GBP currency.
CT052	   | Requested Execution Date is not far enough in the future
CT053	   | End to End ID invalid, it must follow GBP STANDARD BACS Direct Credit payments rules.
CT054	   | This transaction exceed your configured limit for the specified execution date. Please contact your bank.
CT055	   | Creditor reference invalid, it must follow GBP STANDARD BACS Direct Credit payments rules.
CT056	   | Creditor reference invalid, it must follow GBP EXPRESS UK FASTER PAYMENTS payments rules.
CT057	   | HCM file processing not allowed for the provided data and current Originator configuration.
CT058	   | Beneficiary Bank is not reachable for EXPRESS payments
CT059	   | Beneficiary Bank BIC is required for EXPRESS payments
CT060	   | Originator Bank BIC is required for EXPRESS payments
CT061	   | Requested execution date is not a working day
CT070	   | The Collection batchBooking indicator must be false for non-Nuapay originators
CT071	   | The Collection's totalAmount must be equal to the sum of transaction amounts
CT072	   | The Collection's numberOfTransactions must be equal to the sum of transactions
CT073	   | Address Line 1 is not allowed when Street Name is provided.
CT074	   | Domestic Account Number is required if IBAN is not provided
CT075	   | Remittance Information invalid, for GBP Express payments must follow [a-zA-Z0-9-/?:().,+#=!%&*<>;{}@ "'] {0,140}
CT076	   | IBAN is required if External Account Validation is off
CT077	   | Either Iban or Domestic Account is allowed.
CT078	   | Domestic Bank Code is required for provided Account Country.
CT079	   | Domestic Bank Code is not allowed for provided Account Country.
CT080	   | Domestic Branch Code is required for provided Account Country.
CT081	   | Domestic Branch Code is not allowed for provided Account Country.
CT082	   | Domestic Checksum is required for provided Account Country.
CT083	   | Domestic Checksum is not allowed for provided Account Country.
CT084	   | UltimateCreditor either 'organisationId' or 'privateId' is allowed.
CT085	   | UltimateCreditor OrganisationId either 'bicOrBei' or 'other' is allowed.
CT086	   | UltimateCreditor OrganisationId Other SchemeName either 'code' or 'proprietary' is allowed.
CT087	   | UltimateCreditor PrivateId either 'dateAndPlaceOfBirth' or 'other' is allowed.
CT088	   | UltimateCreditor PrivateId Other SchemeName either 'code' or 'proprietary' is allowed.
CT089	   | UltimateDebtor either 'organisationId' or 'privateId' is allowed.
CT090	   | UltimateDebtor OrganisationId either 'bicOrBei' or 'other' is allowed.
CT091	   | UltimateDebtor OrganisationId Other SchemeName either 'code' or 'proprietary' is allowed.
CT092	   | UltimateDebtor PrivateId either 'dateAndPlaceOfBirth' or 'other' is allowed.
CT093	   | UltimateDebtor PrivateId Other SchemeName either 'code' or 'proprietary' is allowed.
CT094	   | StructuredRemittanceInformation cannot be provided in addition to RemittanceInformation
CT095	   | The Collection reference must be unique per originator

<div class="datatable-end"></div>

{% include links.html %}
