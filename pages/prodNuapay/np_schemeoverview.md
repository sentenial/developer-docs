---
title: Scheme Overview
keywords: Scheme SUN CSID Creditor Scheme
summary: "A scheme is a mechanism to differentiate different Direct Debit processing approaches. In SEPA, CORE and B2B are the principal schemes; in the UK Bacs Direct Debit is used"
sidebar: np_sidebar
permalink: np_schemeoverview.html
toc: false
folder: Nuapay
---


## Scheme Overview

Before you can begin to create a mandate/DDI or add Direct Debit payments, you must first decide on the payment scheme that you want to use. 

If you intend to:
* Process EUR payments and your customers are not other businesses or corporate entities, then you'd process through the **SEPA CORE** scheme. 
* Conduct business with other corporates then the **SEPA B2B** scheme may be appropriate. 
* Process GBP payments then you will need to generate DDIs and collect payments through the **Bacs Direct Debit** scheme.

Each scheme has its own distinct requirements. So, for example:

* In B2B there are no refunds possible after 3 business days; for SEPA CORE, payers can request a no-questions-asked refund up to 8 weeks after the inital  <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.collection_date}}">collection date</a>. In Bacs a refund is only possible in specific cases (e.g. the amount or the collection date pre-notified to the payer was incorrect) and there is no time limit on when the refund may be processed. 
* In SEPA your business is identified through a Creditor Scheme Identifier (CSID), in Bacs this identifier is referred to as the Service User Number (SUN).

For more on these differences see the overview table on [Scheme Differences](np_ddpayments.html#scheme-differences).

To decide on what scheme best suits your business, please discuss your requirements with your account manager who will be happy to assist.

|A member of the Nuapay Customer Support team will configure your CSID or SUN for you on both the Sandbox and Production environments.| 


## Using the Scheme in the API

In terms of interacting with the various Mandate/DDI and Direct Debit API services, the scheme you use is essential as it is the foundation on which all your requests are built.

As outlined in the [General API Rules](np_generalrules.html) section, the CSID or SUN is referenced in the URI where, for example, you: 

* Create a mandate/DDI via a POST request: `/schemes/abxq9kq52l/mandates` (note that `abxq9kq52l` is the resource identifier of the scheme in this example)
* Retrieve a Direct Debit through a GET `/schemes/abxq9kq52l/mandates/rtsxq8kaby5/directdebits/eshw2137gfc` (in this case `rtsxq8kaby5` is the mandate identifier; `eshw2137gfc` is the Direct Debit transaction identifier)

To retrieve the [resource identifier](np_generalrules.html#resource-identifiers) for the scheme you want to use in your Nuapay processing, check out the [List Schemes](np_listcredscheme.html) service.

{% include links.html %}
