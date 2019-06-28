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
* Pass a specific API Key unique to each merchant, for authentication
* Originate from an allowed IP address (the allowed IP addresses will be configured for you when you register for the service)
* Include (at a minimum) the mandatory fields required for the specific request that is being made

<p>Specific configurations are also required on the E-Mandate application. Note that specific configurations must be carried out internally by Nuapay staff so please discuss your requirements with a member of our Customer Support team who will be able to assist you in this.</p>

## Resource Identifiers

In order to reference specific Nuapay elements in your API requests, e.g. a mandate or a direct debit, unique resource identifiers must be provided.

For example, assume you have created a Direct Debit transaction under a specific scheme and mandate, with the following attributes:

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

{% include note.html content="The resource identifier for your scheme is essential and is the building block for all subsequent mandate and direct debit calls. Details of how to retrieve your creditor scheme identifier (or SUN for Bacs users) is described in the [List Creditor Schemes](np_listcredscheme.html) section." %}

**Create Mandate**

The Create Mandate service would use the following URI:

|POST `/schemes/abxq9kq52l/mandates`|

(Assume the mandate created has a resource identifier = `rtsxq8kaby5`)

**Retrieve Mandate**

To retrieve that mandate later you would use the following:

|GET `/schemes/abxq9kq52l/mandates/rtsxq8kaby5`|

**Retrieve Direct Debit**

To retrieve the details of the speific transaction created against the mandate, you would use the following:

|GET `/schemes/abxq9kq52l/mandates/rtsxq8kaby5/directdebits/eshw2137gfc`|

For more on these services, see the following:

* [Create Mandate](np_createmandate.html)
* [Retrieve Mandate](np_retrievemandate.html)
* [Retrieve Direct Debit](np_retrievedirectdebit.html)


{% include links.html %}
