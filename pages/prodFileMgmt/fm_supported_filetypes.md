---
title: Supported File Types
keywords: Supported File Types
summary: "It is possible to upload various Direct Debit and Credit Transfer file types. This section describes the most popular file types available"
sidebar: fm_sidebar
permalink: fm_supported_filetypes.html
folder: prodFileMgmt
---

Nuapay supports a number of import file formats for both Direct Debit and Credit Transfer payments.

{% include note.html content="Before you may begin to pass files to the system via REST, you will first need to be configured for the file types that you need on the Nuapay system. Please discuss your requirements and file types required with your Account Manager." %}

## Direct Debit Files

The following file formats are available:

* STD-18 (generally used in the UK for GBP payments but may also be used in Ireland for EUR transactions)
* PAIN.008.001.02
* PAIN.008.001.08
* Nuapay's Generic CSV

{% include tip.html content="Only the most popular file formats are mentioned here. Nuapay can support a number of older flat file formats. If you have a specific format that you would like to process that is not listed here please check with your Account Manager." %}

The STD-18 and PAIN files all follow the rules governing these file formats. For more information, please review the published specifications for these file types.

## The Generic Direct Debit CSV format

If you want to use Nuapay's Generic CSV format, provide the following details in a CSV:

|**Heading**|**Required/Optional**|**Description**|**Format**|
|-------------------------------|-----------------------|-------------------------------------------|----------------------------|
|SepaMandateId| Required| The unique mandate reference. For Bacs, specify the DDI reference.| Max 35 characters Alphanumeric|
|DomesticMandateId| Optional| A secondary mandate reference, which may be ignored| Max 35 characters Alphanumeric|
|CollectionDate|Required| The collection (settlement) date required|Must be provided in YYYY-MM-DD format|
|CollectionAmount|Required| The value of the payment to be collected| Max 12 characters Numeric - 2 decimals.|
|Remittance|Optional |The remittance information for the payment|140 characters Alphanumeric|
|EndToEndId|Conditional|A unique identifier for the transaction. For Bacs, you **must** provide an End-to-end in the format <DDI Reference> + unique alphanumeric code, up to a maximumof 18 characters. If your DDI reference is ABCD123 then your End-to-End should be ABCD123-01, for example.|Max 35 Alpha numeric|
|Reserve1|N/A|Reserve field - not used|N/A|
|Reserve2|N/A|Reserve field - not used|N/A|
|Reserve3|N/A|Reserve field - not used|N/A|
|Reserve4|N/A|Reserve field - not used|N/A|
|Reserve5|N/A|Reserve field - not used|N/A|

A sample CSV would be formatted as below:
```csv
SepaMandateId,DomesticMandateId,CollectionDate,CollectionAmount,RemittanceInfo,EndToEndId,Reserve1,Reserve2,Reserve3,Reserve4,Reserve5
ORI0003569057123,,2024-03-29,1000.50,Remittance Information 1,,,,,,
ORI0003569057822,,2024-03-29,20.90,Remittance Information2,,,,,,
ORI0003569057695,,2024-03-29,3000,Remittance Information3,,,,,,
```

Note:

* The date format may be modified if you open your file in Excel (a date set to 2024-03-29 originally, for example, and saved will be modified in Excel to be 29/03/2024 when the file is reopened later). To avoid this, we recommend that you use a text editor when working with your CSV file. The date must be provided as `YYYY-MM-DD`.
* Where you provide an end-to-end identifier, it must be unique.
* If you do not provide an end-to-end identifier for a SEPA transaction, the system will automatically generate one.
* You must provide an end-to-end for Bacs transactions and it must begin with the DDI reference and be a maximum of 18 characters. See [The DDI Reference and End-to-End Identifiers in Bacs](np_createmandate.html#the-ddi-reference-and-end-to-end-identifiers-in-bacs) for more details on this.

## Credit Transfer Files

The following file formats are available:

* STD-18 (generally used in the UK for GBP payments but may also be used in Ireland for EUR transactions)
* PAIN.001.001.03
* PAIN.001.001.09
* Nuapay's Generic CSV

The STD-18 and PAIN files all follow the rules governing these file formats. For more information, please review the published specifications for these file types.

## The Generic Credit Transfer CSV format

{% include tip.html content="The Generic CSV for CT payments is only available for SEPA CT transactions." %}

If you want to use Nuapay's Generic CSV format, provide the following details in a CSV:

| **Heading**                   | **Required/Optional** | **Description**                           | **Format**                 |
|-------------------------------|-----------------------|-------------------------------------------|----------------------------|
| BeneficiaryName               | Required              | Beneficiary's Name                        | Text 70                    |
| BeneficiaryAddressLine1      | Optional              | Beneficiary's Address Line 1              | Text 70                    |
| BeneficiaryAddressLine2      | Optional              | Beneficiary's Address Line 2              | Text 70                    |
| BeneficiaryAddressCity/Town  | Optional              | City/Town of Beneficiary's Address        | Text 35                    |
| BeneficiaryAddressPostCode   | Optional              | Postal Code of Beneficiary's Address      | Text 16                    |
| BeneficiaryAddressState/Province/County | Optional   | State/Province/County of Beneficiary's Address | Text 35           |
| BeneficiaryAddressCountry    | Optional              | Country of Beneficiary's Address          | ISO3166 Country Code 2    |
| DescriptionofPurpose         | Optional              | Description of Payment Purpose            | Text 140                   |
| BeneficiaryemailAddress      | Optional              | Beneficiary's Email Address               | Text 254                   |
| BeneficiaryPhoneNumber       | Optional              | Beneficiary's Phone Number                | Text 50                    |
| BeneficiaryMobilePhone       | Optional              | Beneficiary's Mobile Phone Number         | Text 50                    |
| BeneficiaryLanguage          | Optional              | Beneficiary's Language                    | Enumeration. May be one of: EN, FR, DE, ES, NL, IT|
| DomesticAccountCountry       | Optional              | Country of Domestic Account               | ISO3166 Country Code 2    |
| DomesticBankCode             | Optional              | Domestic Bank Code                        | Text 70                    |
| DomesticBranchCode           | Optional              | Domestic Branch Code                      | Text 70                    |
| DomesticAccountNumber        | Optional              | Domestic Account Number                   | Text 70                    |
| DomesticAccountChecksum      | Optional              | Domestic Account Checksum                 | Text 35                    |
| BeneficiaryAccountBIC        | Optional              | Beneficiary's Account BIC                 | Text 11                    |
| BeneficiaryAccountIBAN       | Required              | Beneficiary's Account IBAN                | Text 35                    |
| OriginatorAccount            | Required              | Originator's Account                      | Text 70                    |
| RequestedExecutionDate       | Required              | Requested Execution Date                  | Must be provided in YYYY-MM-DD format|
| PaymentAmount                | Required              | Payment Amount                            | Decimal 12 (Fraction=2)    |
| PaymentReference             | Optional              | Payment Reference                         | Text 35                    |
| RemittanceInformation        | Optional              | Remittance Information                    | Text 140                   |
| PaymentFrequency             | Optional              | Payment Frequency                         | Text 11                    |
| ReserveField1                | Optional              | Reserved Field 1                          | Text 140                   |
| ReserveField2                | Optional              | Reserved Field 2                          | Text 140                   |
| ReserveField3                | Optional              | Reserved Field 3                          | Text 140                   |
| ReserveField4                | Optional              | Reserved Field 4                          | Text 140                   |
| ReserveField5                | Optional              | Reserved Field 5                          | Text 140                   |


A (basic) sample CSV would be formatted as follows:
```csv
BeneficiaryName,BeneficiaryAddressLine1,BeneficiaryAddressLine2,BeneficiaryAddressCity/Town,BeneficiaryAddressPostCode,BeneficiaryAddressState/Province/County,BeneficiaryAddressCountry,DescriptionofPurpose,BeneficiaryemailAddress,BeneficiaryPhoneNumber,BeneficiaryMobilePhone,BeneficiaryLanguage,DomesticAccountCountry,DomesticBankCode,DomesticBranchCode,DomesticAccountNumber,DomesticAccountChecksum,BeneficiaryAccountBIC,BeneficiaryAccountIBAN,OriginatorIban,RequestedExecutionDate,PaymentAmount,PaymentReference,RemittanceInformation,PaymentFrequency,ReserveField1,ReserveField2,ReserveField3,ReserveField4,ReserveField5
John Smith,,,,,,,,,,,,,,,,,,CY17002001280000001200527600,IE63AIBK93106511111234,2024-03-29,326,,Remittance Info,,,,,,
Jane Doe,,,,,,,,,,,,,,,,,,NL69INGB0123456789,IE63AIBK93106511111234,2024-03-29,629.38,,Remittance Info,,,,,,
Max Mustermann,,,,,,,,,,,,,,,,,,DE25370502991000122343,IE63AIBK93106511111234,2024-03-29,642,,Remittance Info,,,,,,
```

Note:

* Only SEPA CT is supported.
* The date format may be modified if you open your file in Excel (a date set to 2024-03-29 originally, for example, and saved will be modified in Excel to be 29/03/2024 when the file is reopened later). To avoid this, we recommend that you use a text editor when working with your CSV file. The date must be provided as `YYYY-MM-DD`.
* Where you provide a payment reference, it must be unique.
* If you do not provide a payment reference, the system will automatically generate one.
