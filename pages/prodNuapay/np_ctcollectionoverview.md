---
title: Credit Transfer Collection
keywords: Credit Transfer Collections
summary: "It is possible to initiate multiple CT transactions via a single CT Collection request. A CT Collection is a batch of CT transactions and allows you to process multiple payments in one go."
sidebar: ct_sidebar
permalink: np_ctcollectionoverview.html
folder: prodNuapay
---

Credit Transfer (CT) collections are batches of CT payments that may be initiated via a single REST request.

* You can create and manage collections of credit transfer (CT) payments using the dedicated API endpoints. See the [CT Collection API](np_ctcreatecoll.html).
* These endpoints allow you to submit multiple CT payments in a single request, track the progress of the entire collection, and retrieve details about individual CTs within the collection.

Using CT Collections offers several advantages over creating individual, or "one-shot," CTs. For instance:

* You can streamline the payment process, particularly when dealing with large volumes of payments.
* You can gain a consolidated view of the processing status for all CTs within a collection.

It is important to consider that:

* Collections introduce added complexity compared to one-shot CT creation.
* It's crucial to implement robust error handling and monitoring to ensure smooth processing of all CTs within a collection.

{% include tip.html content="If you are unsure if CT Collections are right for you, please discuss your requirements with your Account Manager who will be happy to assess your needs and suggest the best approach and APIs for your specific business." %}
