---
title: Re-present Failed Direct Debits
keywords: Re-present Failed Direct Debits
summary: "Re-present Failed Direct Debits RESTful API"
sidebar: np_sidebar
permalink: np_representfaileddds.html
folder: prodNuapay
toc: false
---

## API Details

Where a payment fails (for example for insufficient funds) you may want to re-try (i.e. re-present) the payment.

The re-present request carries out two distinct steps:

* It updates the original failed payment's status to `RE-PRESENTED`
* It creates a new Direct Debit payment (with a new collection date and a new payment reference) in `READY_FOR_EXPORT` status

Optionally the new Direct Debit payment may also include a re-presentation fee

For **SEPA**:
{% include note.html content="Certain **SEPA Response codes** will indicate that a re-presentation will be unsuccessful. For example an MD07 (debtor deceased) or an AC04 (Account closed). We recommend that you only attempt to re-present a failed payment for MS03 (Reason not specified) and AM04 (Insufficient funds). " %}

For **Bacs**:
{% include note.html content="For **Bacs** re-presentation must take place within one month of the date on which the first presentation was made; the amount must be the same as the original failed payment. A service user should give at least 5 working days' notice to the payer of the new collection date. For more information on the rules on re-presentation see the Bacs Service User Guide, available for download from the [Bacs site](https://www.bacs.co.uk/)" %}

The following are optional arguments:

* `representationDate`
* `representationFee` (not allowed for Bacs)
* `endToEndId`

{% include important.html content="If you do not specify a re-presentation date or fee, the default values will be taken from your organisation's Nuapay configuration. These settings are configured at the Scheme level for your business."%}

{% include idempotency.html %}


{% include swagger_np.html %}

{% include urls.html %}

{% include tip.html content="You must use the resource identifier of the `schemeId`/ `mandateId`/ `directDebitId` in your requests and not the actual creditor scheme ID/SUN or Unique Mandate Reference or Direct Debit identifier. Resource identifiers are short alphanumeric strings, similar to this: abxq9kq52l. Depending on the request you may need 1, 2 or all 3 of these resource identifiers in your URI." %}

<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/representDirectDebitUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>

{% include links.html %}
