---
title: Cancel Mandate / DDI
keywords: sample
summary: "Cancel Mandate RESTful API"
sidebar: np_sidebar
permalink: np_cancelmandate.html
folder: prodNuapay
toc: false
---

## API Details

How a Mandate/DDI can be cancelled varies between the SEPA and Bacs schemes.

Common to both schemes:

* It is only possible to cancel a mandate/DDI that is in `ACTIVE` status.
* Any `READY FOR EXPORT` Direct Debit transactions linked to a cancelled Mandate/DDI are automatically revoked.
* No further collections may be made against a cancelled mandate/DDI.

In **SEPA** If you want to engage with your payer at a later point, and want to collect direct debit payments once again, you will need to create a new mandate.

In **Bacs**, it is possible for your payers to reinstate a cancelled DDI through their bank, provided that the DDI was cancelled within the last 2 months.
Where this happens, Nuapay will receives a code "R" in an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.addacs}}">ADDACS</a> file and will set the DDI status back to `ACTIVE`. See the [ADDACS Reason Codes](np_bacsreasons.html#addacs-reason-codes) for more information.

## SEPA Mandate Cancelation
In SEPA:
* A mandate may only be cancelled by the merchant.
* If payers want to cancel their mandates they must contact the merchant and request this.
* Mandate cancellations are always **merchant-initiated**.

{% include note.html content="A payer may request that his/her bank refuse a Direct Debit payment for a specific mandate but the payer's bank do not have the power to cancel a mandate (as, unlike in Bacs, it is not stored with the bank). Where a payer refuses a Direct Debit payment this will result in an MS02 SEPA reject. Where you receive a Refusal you should contact your payer to attempt to resolve the issue. " %}


## Bacs DDI Cancelation
In the Bacs scheme, payers may cancel their DDIs by:  

1. Contacting you, the merchant, and requesting that you cancel the DDI.
1. Contacting their bank and requesting the cancellation.

**CONTACTING YOU - Merchant-Initiated**

Where the payer contacts your support team or Account manager and requests the cancellation:

* Call the Cancel DDI endpoint; the DDI is cancelled in Nuapay.
* This update in DDI status automatically triggers a status update from Nuapay to the Bacs scheme (via an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.auddis}}">AUDDIS</a> message: Bacs code `OC`).
* The payer's bank processes this update from Nuapay (via the scheme) and updates the DDI status to Cancelled on its systems.

**CONTACTING THE BANK - Payer-Initiated**

Where the payer goes directly to the bank to request the DDI cancellation:

* The Payer requests the bank to cancel the DDI that was set up with your business.
* The bank will cancel the DDI and issue a message to the Bacs scheme to notify Nuapay via an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.addacs}}">ADDACS</a> notification (Bacs Code = `1`).
* Once Nuapay processes the ADDACS file, the DDI is updated to `CANCELLED` status; you will generally be unable to make collection against that DDI in future.
* (In some cases your payer may look to reactivate the mandate: this can be done if they request reinstatement at their bank within 2 months of the cancellation).

{% include tip.html content="You may want to configure the [Mandate Cancel Event](np_whmandcancel.html) Webhook so that you are notified where a payer-initiated DDI cancelation occurs (at the payer bank)." %}

{% include swagger_np.html %}

{% include urls.html %}
{% include tip.html content="You must use the resource identifier of the `schemeId` in your request and not the actual creditor scheme ID or SUN. This identifier will be similar to this: abxq9kq52l. Similarly, the mandate identifier is the resource identifier (e.g., rtsxq8kaby5) and is not the actual unique mandate reference - so in this case you would call POST /schemes/abxq9kq52l/mandates/rtsxq8kaby5/cancel" %}


<ul id="profileTabs" class="nav nav-tabs">


</ul>

{% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/cancelMandateUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
