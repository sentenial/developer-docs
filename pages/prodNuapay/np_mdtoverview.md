---
title: Mandate Overview
keywords: sample
summary: "You can seek your payers' permission to debit their accounts with a paper mandate or via an e-mandate. Our APIs allow you to work with either approach."
sidebar: np_sidebar
permalink: np_mdtoverview.html
toc: false
folder: product2
---


## Mandate Overview

Our API offers access to standard and electronic mandates (E-Mandates).

If you require your payers to sign paper mandates then the standard mandate approach would be appropriate. Please contact a member of our Customer Services team for more details.

For more information on E-Mandates please check out the various <a href="em_overview.html">E-Mandate implementation options</a>.


## What is an E-Mandate?

Working with paper-based mandates can be problematic; you need to use standard post; your payers may be slow to return the signed mandate; they may make an error when writing their IBAN; in some cases the signature may be unreadbale or the payer may have incorrectly completed the form. Assuming the mandate is returned and has been completed correctly, you then need to store the paper mandates and ensure that they can be retrieved later if required (to defend an unathorised Refund - see MD01 in the <a href = "np_separeasons.html">SEPA Reason Codes</a> section).

Electronic mandates remove all these pain points:

* Users sign the mandates online
* Account details are validated in real time (so your payers cannot provide you with an invalid account number)
* The mandate is set to <b>ACTIVE</b> status immediately so you can begin to take payments right away: no waiting for signed paper mandates to arrive
* Your users receive emails to confirm activation of their mandates so again, less admin work for you!
* Mandate details can be easily retrieved at any time via the <a href = "np_listmandates.html">List Mandates</a> service.

{% include links.html %}
