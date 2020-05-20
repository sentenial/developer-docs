---
title: Mandate/DDI Overview
keywords: sample
summary: "You can seek your payers' permission to debit their accounts with a paper mandate/DDI or via an e-mandate. Our APIs allow you to work with either approach."
sidebar: np_sidebar
permalink: np_mdtoverview.html
toc: false
folder: product2
---


## Mandate/DDI Overview

Our API offers access to standard and electronic mandates/DDIs (E-Mandates).

If you require your payers to sign paper mandates then the standard mandate/DDI approach would be appropriate. Please contact a member of our Customer Services team for more details.

For more information on E-Mandates please check out the various <a href="em_overview.html">E-Mandate implementation options</a>.

## DDI Lodgement

{% include note.html content="DDI Lodgement refers to the **Bacs** Scheme." %}

In the Bacs scheme, new signed DDIs must be lodged and validated with the payers' banks before collections may be made against them. Bacs offer an automated electronic process to register/lodge these DDIs called the Automated Direct Debit Instruction Service (AUDDIS). When your payers sign a DDI, Nuapay will automatically include it in an AUDDIS submission. AUDDIS submissions are generated daily from Nuapay (Monday to Friday).

This is the lifecycle of a DDI:

* A DDI is created in `PENDING` status.
* The payer signs the DDI and Nuapay moves its status to `READY FOR EXPORT`.
* Once per day, Nuapay picks up all `READY FOR EXPORT` DDIs and includes them in an AUDDIS submission file, which is passed to Bacs; at this point the DDI status is updated to `EXPORTED`
* Bacs operates on a 3- to 4-business day cycle (see below) so when the scheme receives the AUDDIS file from Nuapay it processes all the DDIs contained in it and lodges the instructions with the various payers' banks.
* Where there are issues with a submission (e.g. the account provided does not allow Direct Debit payments to be taken, for example), Bacs will inform Nuapay via an AUDDIS response file and that DDI will be automatically updated to `CANCELLED`
* Where there is no issue, the DDI is deemed to be successfully lodged and its status is updated to `ACTIVE`. Once a DDI is in Active status, Direct Debit payments may be made against it.

See [Mandate/DDI Statuses](np_mandatestatuses.html) For more information on the various statuses.

## AUDDIS Processing Cycle

|**Day1**|**Day2**|**Day 3**|**Day 4**|
|**Thursday**|**Friday**|**Monday**|**Tuesday**|
|Nuapay transmits the AUDDIS file to Bacs|Bacs passes valid DDIs to the paying banks|Valid DDIs are lodged against payers' accounts; details of invalid DDIs are passed to Nuapay |(Similar to Day 3) Valid DDIs are lodged, invalid DDIs are passed back to Nuapay and their status is updated to `CANCELLED`|

## Mandate Lodgement in the B2B Scheme

{% include note.html content="In SEPA, mandate Lodgement is only required for the **SEPA B2B** Scheme; this **is not a requirement for the SEPA CORE scheme**" %}

After signing a B2B Mandate, your payer must inform his/her bank of the mandate setup. Depending on the bank, it may be possible to do this online but every bank will have its own method to allows its customers to lodge their B2B mandates. (Unlike in the Bacs scheme, there is no automated process for this).

Before they can process a B2B Direct Debit, your payer's bank must:
* Confirm that the mandate details provided to them are correct and have been confirmed and authorised by the payer.
* Check the  first and the subsequent Collections against the stored Mandate data.
* Ensure that their clients are aware that the bank must be informed of any amendments or cancellations of the mandate.

{% include warning.html content="It is up to the B2B payer to confirm to his/her bank that he/she has signed a B2B mandate with a specific merchant before collections commence. We strongly recommend that you, as the merchant, inform your payers that this is an additional step that must be performed before collections can be made on the B2B mandate. Your payers will need to confirm with their banks when their mandates have been successfully lodged so that you can begin to collect payments." %}


## E-Mandate Benefits

Working with paper-based mandates can be problematic; you need to use standard post; your payers may be slow to return the signed mandate; they may make an error when writing their account details; in some cases the signature may be unreadbale or the payer may have incorrectly completed the form. Assuming the mandate/DDI is returned and has been completed correctly, you then need to store the paper mandates and ensure that they can be retrieved later if required.

Electronic mandates remove all these pain points:

* Users sign the mandates online
* Account details are validated in real time (so your payers cannot provide you with an invalid account number)
* The mandate is set to **ACTIVE** status immediately (for the SEPA CORE scheme) so you can begin to take payments right away: no waiting for signed paper mandates to arrive. Note that for BACS, DDIs are subject to the lodgement and collection cycle so mandates do not go into ACTIVE status immediately (see the previous section).
* Your users receive emails to confirm activation of their mandates so again, less admin work for you!
* Mandate/DDI details can be easily retrieved at any time via the [List Mandates](np_listmandates.html) service.

{% include links.html %}
