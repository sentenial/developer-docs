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

The Retrieve Verification request allows you to:

* Pass the `verificationId`, returned in the response from the [Request Verification](ver_reqverification.html) endpoint.
* Retrieve the `nameScore` in the `results` object.
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


{% include swagger_np.html %}

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
