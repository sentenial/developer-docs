---
title:  "Credit Transfer Enhancements!"
published: true
permalink: ct-updates.html
sidebar: productOverview_sidebar
summary: "Asynchronous CT processing and CT Collections (Batches) have been introduced in the v8.42 release"
tags: [news]
---

## Asynchronous CT processing

In today's fast-paced digital world, the need for efficient and scalable payment processing is more critical than ever. Traditional synchronous processing, where each request must be completed before the next one can be initiated, often struggles to keep up with high-volume demands, such as payroll processing for large companies. This is where **asynchronous credit transfer (CT) processing** comes into play, offering a solution that significantly enhances efficiency and scalability.


<img src= 'images/news_async.png'>


So, what's the magic behind asynchronous processing?

Imagine sending a large batch of payments. Instead of waiting for each payment to be processed individually, the system can accept all the requests upfront and process them in the background.

This frees up resources and allows for faster response times, even during peak hours.

## What are the key benefits of adopting an asynchronous approach?

Firstly, it eliminates the bottlenecks associated with synchronous processing, allowing systems to handle a much higher volume of requests without compromising performance.

Asynchronous processing effectively decouples the request initiation from the actual processing, leading to a smoother user experience and improved overall system responsiveness.

Secondly, it allows for greater flexibility in handling errors or exceptions. Should a payment encounter an issue during processing, it can be flagged and addressed separately without halting the entire batch.

Overall, asynchronous CT processing represents a paradigm shift in payment processing, allowing businesses to meet the demands of today's high-volume, fast-paced digital landscape.

### CT Collections

Tired of initiating numerous payments individually? Our new Credit Transfer Collections functionality allows you to create a batch of payments with just one request! This streamlines your payment process, saving you valuable time and effort.

Each collection is assigned a status, starting with 'QUEUED' upon creation, and progressing through various stages such as 'PENDING,' 'INITIATED,' 'PENDING_SETTLEMENT,' and ultimately reaching either 'COMPLETE,' 'COMPLETE WITH ERRORS,' or 'REJECTED.' You can track the progress of individual payments within a collection List CT Collections Endpoint.

To ensure a seamless experience, robust validation checks are performed at each stage of the collection process. These validations are designed to catch any potential errors early on, preventing unnecessary processing of faulty collections. Detailed error reporting is provided, allowing you to quickly identify and rectify any issues.




{% include links.html %}
