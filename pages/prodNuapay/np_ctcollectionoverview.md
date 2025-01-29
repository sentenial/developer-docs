---
title: Credit Transfer Batches
keywords: Credit Transfer Batches
summary: "It is possible to initiate multiple CT transactions via a single CT Batch request. A CT Batch is a collection or group of CT transactions and allows you to process multiple payments in one go."
sidebar: ct_sidebar
permalink: np_ctcollectionoverview.html
folder: prodNuapay
---

Credit Transfer (CT) batches are groups or collections of CT payments that may be initiated via a single REST request.

* You can create and manage batches of credit transfer (CT) payments using the dedicated API endpoints. See the [CT Batch API](np_ctcreatecoll.html).
* These endpoints allow you to submit multiple CT payments in a single request, track the progress of the entire batch, and retrieve details about individual CTs within the batch.

Using CT batches offers several advantages over creating individual, or "one-shot," CTs. For instance:

* You can streamline the payment process, particularly when dealing with large volumes of payments.
* You can gain a consolidated view of the processing status for all CTs within a batch.

It is important to consider that:

* Batches introduce added complexity compared to one-shot CT creation.
* It's crucial to implement robust error handling and monitoring to ensure smooth processing of all CTs within a batch.

{% include tip.html content="If you are unsure if CT Batches are right for you, please discuss your requirements with your Account Manager who will be happy to assess your needs and suggest the best approach and APIs for your specific business." %}
