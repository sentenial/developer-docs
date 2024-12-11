---
title: Application Reason Codes
keywords: Application Reason Codes
summary: "When processing transactions via file, a number of application errors are possible: these are sometimes referred to as Technical Errors and are generated prior to payments being passed to Clearing for further processing"
sidebar: resources_sidebar
permalink: np_appreasons.html
folder: prodNuapay
toc: true
datatable: true
---

Application error codes are possible for Credit Transfer and Direct Debit Transactions.

### Credit Transfer Application Error codes

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
CT096	   | Credit Transfer is not in a valid status to be Recalled.
CT097	   | Credit Transfer can not be recalled as it is a part of HCM batch.

<div class="datatable-end"></div>
### CT Collection Application Error codes

<div class="datatable-begin"></div>

| Code   | Description                                                                                                                                                                                                                                        |
|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CTC001 | All transactions in the collection have been rejected or failed. This code indicates that every attempted credit transfer within the collection has been unsuccessful, for one reason or another. This is a general code; more information is needed to determine the specific reason for each individual credit transfer failure. |
| CTC002 | Originator Account provided does not exist, or is not in a valid status. The Originator Account either does not exist or is not in the correct status (possibly locked or closed) to initiate credit transfers.                                  |
| CTC003 | Requested payment type is not supported by Originator. The payment type specified in the collection request is not supported by the Originator Account.                                                                                          |
| CTC004 | Originator account currency does not match payment currency. The currency of the Originator Account does not match the currency of the payment requested in the collection.                                                                      |
| CTC005 | Credit transfer not allowed at the moment due to account settlement. The Originator Account is currently undergoing settlement and cannot be used to initiate credit transfers.                                                                  |
| CTC006 | Credit transfer not available from this account. The Originator Account is not eligible to initiate credit transfers. This could be due to account restrictions or configuration settings.                                                      |
| CTC007 | The Collection batchBooking indicator must be false for non-Nuapay originators. The collection request has batchBooking set to true, but the Originator Account does not belong to a Nuapay customer. Non-Nuapay originators cannot use the batch booking feature. |
| CTC008 | Originator Bank BIC is required for EXPRESS payments. The collection request includes a payment with type EXPRESS, but the Originator Account does not have a Bank Identifier Code (BIC). A BIC is necessary to process EXPRESS payments.       |
| CTC009 | Requested payment type is not supported by Originator. |
| CTC010 | Requested execution date is today, and Cut-off time has passed. The requested execution date for the credit transfer is today's date, but the cut-off time for processing payments for that day has already passed.                              |
| CTC011 | Requested execution date is not a working day. The requested execution date for the credit transfer falls on a non-working day, such as a weekend or bank holiday.                                       |
| CTC012 | Requested execution date is in the past. The requested execution date for the credit transfer is a date that has already occurred.                                                                        |
| CTC013 | The Execution Date must be set to today's date. The execution date for the credit transfer must be set to the current date.                                                                                |
| CTC014 | Requested Execution Date is not far enough in the future. The requested execution date does not meet the minimum future date requirements for the specified payment type. Some payment types require a certain number of days to process.       |
| CTC015 | The collection has been rejected due to insufficient funds. The Originator Account does not have enough funds to cover the total amount of the requested collection of credit transfers. This code usually applies to collections with batch booking enabled. |
| CTC016 | Processing Failed. Unexpected Error. A general error code signifying an unexpected error occurred during the processing of the collection.                                                                                                        |

<div class="datatable-end"></div>

### Direct Debit Application Error codes

<div class="datatable-begin"></div>

Code       | Description                                                                  
---------- | ----------------------------------------------------------------------------
DD001	   | Mandate referenced in Payment File does not exist.
DD002	   | The SEPA Mandate ID and Domestic Mandate ID provided do not match to an existing mandate
DD003	   | The Requested Collection Date for the Transaction is not valid
DD004	   | The Data Code on the Payment must reflect the Scheme to which the payment is being added.80 or 90 for Core 70 for B2B"
DD005	   | The Payment scheme referenced in the Payment does not match the Mandate Payment Scheme.Ensure that both the Payment and the Mandate are added for the same scheme, Core or B2B."
DD006	   | The Transaction Count in the Batch trailer is incorrect
DD007	   | The Transaction Sum in the Batch trailer is incorrect
DD008	   | The Account number Sum in the Batch trailer is incorrect
DD009	   | Remittance information should not be longer then 140 characters.
DD010	   | The File Reference is invalid or not unique
DD011	   | Duplicate File
DD012	   | The Transaction Count in the file is incorrect
DD013	   | The Transaction Sum in the file is incorrect
DD014	   | The Reference ID Sum in the trailer is incorrect
DD015	   | The Reversal Count in the trailer is incorrect
DD016	   | The Reversal Sum in the trailer is incorrect
DD017	   | The Reversal ID Sum in the trailer is incorrect
DD018	   | The Transaction is marked as a reversal which is not currently supported in Origix
DD019	   | The scheme selected on UI should match with the file scheme type
DD020	   | Each Payment in a Spanish CSB 058 file must contain an Individual Record type 6
DD021	   | The Originator Account referenced within the payment file is invalid. Please ensure the Originator Account has been added to the originator scheme before adding a payment.
DD022	   | The Originator Account referenced within the payment file does not exist within the system. Please ensure the Originator Account has been added to the originator scheme before adding a payment.
DD023	   | No mandate can be found to match the details provided in the payment file.
DD024	   | The Debtor Account referenced within the Payment file does not exist within any Mandates within the Upload Scheme.
DD025	   | Reason code not available from bank status update.
DD026	   | Invalid transaction amount
DD027	   | The End to End ID in the file is not Unique
DD028	   | Invalid Payment Reference
DD029	   | Duplicate Payment Reference
DD030	   | A DD exists with generated End to End Reference
DD031	   | Country code provided is not a valid ISO 3166-1 alpha-2 code

<div class="datatable-end"></div>


{% include links.html %}
