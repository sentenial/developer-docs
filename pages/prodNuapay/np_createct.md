---
title: Create Credit Transfer
keywords: Create Credit Transfer
summary: "Create Credit Transfer RESTful API"
sidebar: np_sidebar
permalink: np_createct.html
folder: prodNuapay
toc: true
---

## API Details

{% include important.html content="The [JWS-Signature header](np_secjws.html) is required for this endpoint. " type="primary" %}


{% include tip.html content="Before you can generate a Credit Transfer (CT) payment, using this API request, you must first [Create a Beneficiary](np_createbeneficiary.html). Alternatively you can use the [Create Credit Transfer & Beneficiary](np_createctandbene.html) to create the payee and the payment in one API request." %}

{% include idempotency.html %} 


## SEPA Credit Transfers

When creating SEPA Credit Transfer (also referred to as an SCT or CT) payments, note that:

* Payments are processed for **EUR currency payments only**
* CT payments, unlike Direct Debit payments, do not require that the transaction is passed to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.clearing}}">SEPA Clearing system</a> days in advance of the collection date.
* If you create your CT payment early enough on a specific working day (before 8AM GMT), the funds will typically be credited to your beneficiary on the same day. (See the Important Note below for more on this).
* If you create the payment later in the day then the CT will generally be credited to the beneficiary on the following business day.

{% include important.html content="A Note on GMT: Nuapay apply Daylight Savings Time (DST) during the summer months (which is commonly referred to as British Summer Time (BST)). BST runs from the last Sunday in March to the last Sunday in October. During this period the cut off time is actually GMT -1 (so 07:00 GMT); during the period from November to the end of March, the cut off time is 08:00 GMT." type="primary" %}

## Faster Payments

The Faster Payments Scheme (FPS) is an instant payment scheme (with funds being credited to the beneficiary generally in a matter of seconds) available in the UK.
Note that FPS:

* Is available for **GBP curency payments only**.   
* Unlike SEPA CT, FPS is a 24/7/365 system.
* Requires the following values in your request:
  * `paymentCurrency` = GBP.
  * `type` = EXPRESS

## Payment Types

Payments can have a `type`:

* STANDARD
* EXPRESS
* FASTEST_POSSIBLE

|**Currency**|**Default Type**|**CT Type**|
|EUR|`STANDARD`| SCT |
|EUR|`EXPRESS` | SCT Instant|
|GBP|`STANDARD`| Bacs Direct Credit|
|GBP|`EXPRESS`| FPS|

By default EUR payments are processed as `STANDARD`; GBP payments are processed as `EXPRESS`.

Where you specify `FASTEST_POSSIBLE` a payment will go via the Express channel if possible; if it is not possible to send the payment as Express then the transaction will be processed as a Standard payment.

{% include note.html content="If you have 2 or more Nuapay accounts configured and want to transfer funds between these accounts you will need to use the [Transfer Between Accounts](np_accounttransfer.html) service" %}

## Remittance Information

Remittance Information allows you to specify details of the payment to your beneficiary.

* This information may be used for reconciliation and will be displayed on the payee's bank statement.
* Remittance can be passed in one of two fields.

Depending on the currency of the payment, use the correct remittance value as outlined in the table below:

|**Currency**|**Field**|**Details**|
|GBP|`structuredRemittanceInformation.creditorReference`|While 35 characters are possible, only 18 will be used (as per the Faster Payments scheme rules). If you provide > 18 characters, the remittance text will be truncated and only 18 will be passed in your request.|
|EUR|`remittanceInformation`|Up to a maximum of 140 characters may be used.|


{% include note.html content="Passing Remittance is optional and only one instance of either `remittanceInformation` (for EUR) or `structuredRemittanceInformation.creditorReference` (for GBP) should be passed in your request; if both values are provided, you will receive a validation error." %}




**Supported Characters**

Remittance can use the following characters:

* All alphanumeric characters (upper- and lower-case).
* A set of special characters.

The following are all allowed:

|a b c d e f g h i j k l m n o p q r s t u v w x y z|
|A B C D E F G H I J K L M N O P Q R S T U V W X Y Z|
|0 1 2 3 4 5 6 7 8 9|
|/ - ? : ( ) . , ' + Space|

{% include tip.html content="For Faster Payments (GBP) the following special characters are also allowed: # (hash), = (equals), ! (exclamation mark), “ (right double quote), % (percentage), & (ampersand), * (asterisk), < (less than), > (greater than), ; (semi colon), { (left curly bracket), @ (at), CrLf (carriage return line feed)." %}


{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addCreditTransferUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>



{% include links.html %}
