---
title: Retrieve Verification
keywords: Retrieve a Verification Request
summary: "Retrieve Verification RESTful API"
sidebar: ver_sidebar
permalink: ver_retrieveverification.html
folder: prodNuapay
toc: false
---

## API Details

## CoP / VoP

The Retrieve Verification request allows you to:

* Pass the `verificationId`, returned in the response from the [Request Verification](ver_reqverification.html) endpoint.
* Retrieve the verification `type`.

The detail of the verification result are provided in the `accountHolderVerificationResult` object. 

Possible `types` include:

* FULL_MATCH
* PARTIAL_MATCH 
* NO_MATCH
* UNABLE_TO_MATCH

| Type | Definition | Likely Causes | Next Steps |
|--------|------------|---------------|------------|
| `FULL_MATCH` | The account details exactly match the records held by the bank. | • All submitted details (name, account number, sort code/IBAN) match bank records | Safe to proceed. You can continue with the payment or add the beneficiary confidently. |
| `PARTIAL_MATCH` | The account details partly align with the records (e.g., surname matches but first name differs). | • Minor spelling differences (e.g., “Jon” vs “John”)<br>• Typo or formatting variation in name<br>• Business/trading name vs registered name<br>• Initials vs full names | Review details carefully. May be acceptable if variation is minor/expected (e.g., business vs trading name). If unexpected, confirm with payee before proceeding. |
| `NO_MATCH` | The account details do not align with what the bank holds. | • Incorrect account name<br>• Typo in account number/sort code/IBAN<br>• Details belong to a different account | Contact payee to confirm details; consider halting payment until resolved. |
| `UNABLE TO MATCH` | The service cannot confirm either way. | • Receiving bank not participating in VoP.CoP<br>• Account type not supported (e.g., savings, pooled, some business accounts)<br>• Temporary technical issue at bank<br>• Incomplete or incorrectly formatted input | Does not mean details are wrong. Proceed with caution; may need manual confirmation from payee. |


## Open Banking AIS

{% include tip.html content="Open Banking AIS-based user verification will be deprecated in November 2025 so we highly recommend using CoP/VoP verification. " %}

The Retrieve Verification request allows you to:

* Pass the `verificationId`, returned in the response from the [Request Verification](ver_reqverification.html) endpoint.
* Retrieve the `nameScore` in the `openBankingVerificationResults` object.
* See the account type: `CACC` - Current Account; `SVGS` - Savings Account, etc. See table below.

In some cases, where the user holds more than one account at the bank, a number of account holder names and scores may be returned in the `results` object of the response.

## Account Types

The following account types may be returned:

|`CACC`|	Current	Account used to post debits and credits when no specific account has been nominated.|
|`CARD`|	CardAccount	Account used for credit card payments.|
|`CASH`|	CashPayment	Account used for the payment of cash.|
|`CHAR`|	Charges	Account used for charges if different from the account for payment.|
|`CISH`|	CashIncome	Account used for payment of income if different from the current cash account.|
|`COMM`|	Commission	"Account used for commission if different from the account for payment.|
|`CPAC`|	ClearingParticipantSettlementAccount	Account used to post settlement debit and credit entries on behalf of a designated Clearing Participant.|
|`LLSV`|	LimitedLiquiditySavingsAccount	Account used for savings with special interest and withdrawal terms. |
|`LOAN`|	Loan	Account used for loans.|
|`MGLD`|	MarginalLending	Account used for a marginal lending facility.|
|`MOMA`|	MoneyMarket	"Account used for money markets if different from the cash account.|
|`NREX`|	NonResidentExternal	Account used for non-resident external.|
|`ODFT`|	Overdraft	Account is used for overdrafts.|
|`ONDP`|	OverNightDeposit	Account used for overnight deposits.|
|`OTHR`|	OtherAccount	Account not otherwise specified. |
|`SACC`|	Settlement	Account used to post debit and credit entries, as a result of transactions cleared and settled through a specific clearing and settlement system.|
|`SLRY`|	Salary	Accounts used for salary payments.|
|`SVGS`|	Savings	Account used for savings.|
|`TAXE`|	Tax	Account used for taxes if different from the account for payment.|
|`TRAN`|	TransactingAccount	A transacting account is the most basic type of bank account that you can get. The main difference between transaction and cheque accounts is that you usually do not get a cheque book with your transacting account and neither are you offered an overdraft facility.|
|`TRAS`|	CashTrading	"Account used for trading if different from the current cash account.|


{% include idempotency.html %}


{% include swagger_ver.html %}

{% include urls.html %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/verification-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/getVerificationRequestUsingGET','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
