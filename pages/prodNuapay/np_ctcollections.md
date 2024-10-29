---
title: Credit Transfer Collections
keywords: Credit Transfer Collections
summary: "The Nuapay Credit Transfer Collection APIs are available as v1 and v2; the v1 version is synchronous, v2 is asynchronous."
sidebar: ct_sidebar
permalink: np_ctcollections.html
folder: prodNuapay
---

There are two versions of the Nuapay CT APIs:

* V1 operates in synchronous mode.
* V2 operates asynchronously

{% include note.html content="In general, only v2 APIs use 'v2' in their URI path. Collection CTs are asynchronous but as they did not have a v1 synchronous version, they do not include a 'v2' in their endpoint path. " %}

## Synchronous vs Asynchronous Processing

In the **synchronous processing model**:
* Each request is fully processed within the same thread before a response is returned.
* This approach, while straightforward, can lead to performance bottlenecks, particularly when handling a large volume of requests.

In the v2 **asynchronous processing model**:

* API requests are received, validated, and queued for processing, allowing the API to immediately return a response to the user.
* This decoupling of request reception and processing results in improved performance and scalability.
* This is especially beneficial for high-volume operations such as payroll runs.

{% include tip.html content="For new users we highly recommend that you use the v2 version of the API. For existing users, who have implemented the v1 API, you may continue to work with the synchronous APIs without any issue." %}
