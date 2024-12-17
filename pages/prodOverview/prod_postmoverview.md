---
title: Postman Overview
keywords: Postman Collections
summary: "Test the Nuapay APIs via Postman."
sidebar: productOverview_sidebar
permalink: prod_postmoverview.html
folder: prodOpenBanking
---

## Nuapay Postman Collection
The Nuapay API Collection is hosted within <a href='https://www.postman.com/nuapayapi/nuapay-api/overview' target='_new'>Nuapay’s public workspace</a> in Postman. You can fork this collection from the public workspace into your own. Head over there to get started.

## Getting Set Up

1. <a href='https://www.nuapay.com/request-api-sandbox/' target = '_new'>Request a Nuapay Sandbox account</a>. The sandbox is our dedicated testing environment where you can build and test your integration without touching real money.
1. Log on to the Nuapay Console to retrieve your API Key from the API Configuration section.

## Getting Started
To get started, create a fork:
<img src= 'images/postm_create_fork.png'>

1. Enter a name for your fork and select the workspace where it will be created.
1. Select the "watch this collection" checkbox to stay up to date with our APIs.

## Authorization
In the Authorization section of the Nuapay collection set the Auth Type to `Basic Auth` and enter your Nuapay API Key as the Username:

<img src = 'images/postm_auth.png'>

## Setting up Your Environment

You'll need to select an environment or create one to store variables from API responses:
1. Select **Create Environment**:

   <img src = 'images/postm_create_env.png'>

1. Environment variables in postman are denoted by a template string with curly braces (e.g. {% raw %}{{variable}} {% endraw %}).
1. Make sure the Nuapay environment is selected in the Environment drop-down in the top right corner of Postman when making requests from the imported collection.

## Point to Note

* You can only run requests for products that our Support team have activated for you.
* The collection does not include all available endpoints. The purpose of the collection is to showcase Nuapay’s product suite. All public endpoints are available to download from our swagger and Open API specs.
*	Our requests are chained together automatically via environment variables, so there is no need to copy & paste IDs across requests.


{% include links.html %}
