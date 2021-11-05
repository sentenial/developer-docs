---
title: Credit Transfer Statuses
keywords: sample
summary: "Credit Transfer transactions move through various statuses in their lifecycle; these are described in this section."
sidebar: np_sidebar
permalink: np_ctstatuses.html
folder: prodNuapay
---


## Overview

Nuapay supports both standard and express Credit Transfer <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.scheme}}">schemes</a> in both EUR and GBP currencies.
* Standard schemes use a file-based approach to pass payments from Nuapay to the required Scheme for processing.
* Express schemes use REST APIs.
* Standard schemes can take from one to two business days to clear; express payments are processed in seconds.  

{% include note.html content="All merchant/partner interactions with Nuapay are via REST. Where a payment is created against a standard file-based scheme, Nuapay will batch those payments into an appropriate file for onward processing. Your interaction in setting up the payment or retrieving its status later, for example, is all done through APIs. " %}

The following table summarises the differences across the supported CT schemes:

|**Currency**|**Type**|**Scheme**|**Availability**|**Underlying Channel**|**Funds Credited**|
|EUR| Standard| SEPA Credit Transfer|Monday - Friday|File-based (<a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.iso_xml}}">ISO XML file</a>)|Typically 1 business day*|
|EUR| Express| SEPA Credit Transfer Instant|24/7/365|APIs|Instantly|
|GBP| Standard| Bacs Direct Credit|Monday - Friday|File-based (<a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.flat_file}}">flat file</a>)|2 Business Days*|
|GBP| Express | Faster Payments|24/7/365|APIs|Instantly|

|* The SEPA Credit Transfer and the Bacs Direct Credit schemes are subject to non-processing dates throughout the year. See [Non-Processing Days](np_businessdays.html) for more details|

{% include tip.html content="If a SEPA Credit Transfer is created early on a business day (before the cut-off time of 08:00 GMT) the payment will typically be credited to the beneficiary on the same day. Note that Nuapay apply Daylight Savings Time (DST) during the summer months (which is commonly referred to as British Summer Time (BST)). BST runs from the last Sunday in March to the last Sunday in October. During this period the cut off time is actually GMT -1 (so 07:00 GMT); during the period from November to the end of March, the cut off time is 08:00 GMT." %}


## All Credit Transfer Statuses

Note that in:
* _EXPRESS_ schemes, transactions can move from `PENDING` to `PENDING_SETTLEMENT` to  `ACCEPTED` (or `REJECTED`).
* _STANDARD_ schemes, transactions can move from `PENDING` to `READY FOR EXPORT` to `EXPORTED` to `ACCEPTED` (or `REJECTED`).


<table>
  <tbody>
    <tr>
      <td><strong>Status</strong></td>
      <td><strong>Description</strong></td>
    </tr>
    <tr>
      <td><code class="language-plaintext highlighter-rouge">PENDING</code></td>
      <td>Future-dated payments are initially created in pending status.
      <ul>
      <li>Based on the scheme rules for <strong>standard payments</strong>, the CT will transition from this status to READY FOR EXPORT.</li>
      <li>Future-dated <strong>Express</strong> payments will transition from this status to PENDING_SETTLEMENT and to ACCEPTED (or REJECTED) on their execution date (at approximately 02:00 GMT)</li>
      </ul></td>
    </tr>
    <tr>
      <td><code class="language-plaintext highlighter-rouge">READY FOR EXPORT</code></td>
      <td>Only applicable for <strong>Standard</strong> schemes:
      <ul>
      <li>The standard CT payment has been created.</li>
      <li>It has not yet been included in a PAIN.001 XML file (SEPA) or a STD-18 payment file (Bacs) </li>       
      </ul></td>
    </tr>
    <tr>
      <td><code class="language-plaintext highlighter-rouge">EXPORTED</code></td>
      <td>Only applicable for <strong>Standard</strong> schemes:
      <ul>
      <li>The standard CT payment has been included in a PAIN.001 file (SEPA) or a STD-18 file (Bacs) and has been passed to Clearing.</li>
      <li>The CT will generally be exported 1 business day prior to the collection date (SEPA) or 2 days in advance (Bacs). </li>
      </ul></td>
    </tr>
    <tr>
      <td><code class="language-plaintext highlighter-rouge">PENDING_SETTLEMENT</code></td>
      <td>Only applicable for <strong>Express</strong> schemes:
      <ul>
      <li>The payment has been passed to the scheme but has not yet transitioned to `ACCEPTED` or `REJECTED`</li>
      <li>This is a an interim status and a payment should only be in this status for a few seconds before transitioning to a final status.</li>
      </ul></td>
    </tr>
    <tr>
      <td><code class="language-plaintext highlighter-rouge">ACCEPTED</code></td>
      <td>Where a payment has not been rejected, The CT status is updated to Accepted on its execution date.
      </td>
    </tr>
    <tr>
      <td><code class="language-plaintext highlighter-rouge">REJECTED</code></td>
      <td>If the payment cannot be made e.g. the beneficiary account is closed, the payment will transition to Rejected.
      <ul>
      <li>The CT payment will transition to this status where a rejection is processed from the beneficiary bank or from the Scheme.</li>
      <li>A CT Rejection results in a credit to the merchant account.</li>
      </ul></td>
    </tr>
    <tr>
      <td><code class="language-plaintext highlighter-rouge">RECALLED</code></td>
      <td>A <strong>standard</strong> payment has been cancelled prior to being sent to the Scheme for further processing.
      <ul>
      <li>A CT payment may be recalled when it is in PENDING or READY FOR EXPORT status.</li>
      <li>The Recall operation is available via the Nuapay User Interface (this is not currently an option via the API).</li>      
      <li>Please contact support should you need to recall a CT payment.</li>
      </ul></td>
    </tr>
    <tr>
      <td><code class="language-plaintext highlighter-rouge">CANCELLED</code></td>
      <td>A <strong>standard</strong> payment has been cancelled AFTER export to the scheme, where the <a href = "np_separeasons.html">SEPA Reason Code</a> is one of the following: `CUST`, `CUTA`, `DUPL`, `UPAY`.
      <ul>
      <li>This status is only applicable to SEPA CT payments.</li>
      <li>It may not always be possible to cancel an EXPORTED CT payment.</li>
      <li>this process requires a manual intervention from the Nuapay Support team to contact the beneficiary bank. </li>
      <li>Please contact support should you need to cancel a CT payment.</li>
      </ul></td>
    </tr>
  </tbody>
</table>



{% include tip.html content="SEPA and Bacs are file-based schemes and once you have created a set of CT payments for a specific execution date, your transactions are combined into either a PAIN.001 XML file (SEPA) or a Standard-18 (STD-18) flat file format (Bacs) and passed to the appropriate Clearing system for further processing. This is all managed in the background for you and you do not need to interact with these files. They are just referenced here to give some background as to when and why statuses transition, especially from `READY_FOR_EXPORT` to `EXPORTED`." %}



{% include links.html %}
