---
title: General API Rules
keywords: API General rules
summary: "The HTTPS protocol, API keys and originator configuration."
sidebar: np_sidebar
permalink: np_generalrules.html
folder: prodNuapay
---

## General Points

<p>Note that all requests must:</p>

* Be sent via the HTTPS protocol
* Pass a specific API Key unique to each merchant, for authentication or an OAuth token.
* Originate from an allowed IP address (the allowed IP addresses will be configured for you when you register for the service)
* Include (at a minimum) the mandatory fields required for the specific request that is being made

{% include note.html content="Our API is backward-compatible. For more details see [Versioning and Backward Compatibility](prod_versioning.html) under the Product Overview section." %}

<p>Specific configurations are also required on the E-Mandate application. Note that these configurations must be carried out internally by Nuapay staff so please discuss your requirements with a member of our Customer Support team who will be able to assist you in this.</p>

## Resource Identifiers

In order to reference specific Nuapay elements in your API requests, e.g. a mandate or a direct debit, unique resource identifiers must be provided.

For example, assume you have created a SEPA Direct Debit transaction under a specific scheme and mandate, with the following attributes:

|**Item**| **Value**|
|Creditor Scheme ID | GB09ZZZSDDBBRU00000055356871SD1|
|Mandate Reference | MAND-12345|
|Direct Debit End-to-End| C5F53BF5-EFA4-4319-8|

When working with this transaction via the API, you will need to reference the **resource identifier** values.
These might be as follows:

|**Item**| **Value**| **Resource Identifier** |
|Creditor Scheme ID | GB09ZZZSDDBBRU00000055356871SD1| abxq9kq52l |
|Mandate Reference | MAND-12345| rtsxq8kaby5 |
|Direct Debit End-to-End| C5F53BF5-EFA4-4319-8| eshw2137gfc |

<div markdown="span" class="alert alert-info" role="alert"><i class="fas fa-info-circle"></i> <b>Note</b>:  The resource identifier for your scheme is essential and is the building block for all subsequent mandate and direct debit calls. Details of how to retrieve your creditor scheme identifier (or <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.sun}}">SUN</a> for Bacs users) is described in the [List Schemes](np_listcredscheme.html) section.</div>


**Create Mandate/DDI**

The Create Mandate/DDI service would use the following URI:

|POST `/schemes/abxq9kq52l/mandates`|

(Assume the mandate created has a resource identifier = `rtsxq8kaby5`)

**Retrieve Mandate/DDI**

To retrieve that mandate later you would use the following:

|GET `/schemes/abxq9kq52l/mandates/rtsxq8kaby5`|

**Retrieve Direct Debit**

To retrieve the details of the specific transaction created against the mandate, you would use the following:

|GET `/schemes/abxq9kq52l/mandates/rtsxq8kaby5/directdebits/eshw2137gfc`|

For more on these services, see the following:

* [Create Mandate/DDI](np_createmandate.html)
* [Retrieve Mandate/DDI](np_retrievemandate.html)
* [Retrieve Direct Debit](np_retrievedirectdebit.html)


{% include links.html %}
