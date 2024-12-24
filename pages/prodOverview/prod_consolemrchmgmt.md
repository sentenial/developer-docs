---
title: Nuapay Console Merchant Management
keywords: Nuapay Console Merchant Management
summary: "Manage Merchants via the Console."
sidebar: productOverview_sidebar
permalink: prod_consolemrchmgmt.html
folder: prodOverview
toc: false
---

{% include note.html content="This section is for Partner users and describes how to manage the Merchants linked to a Partner entity." %}

## View & Configure Merchants

To view merchants:
1. Log on to the Console as a Partner User.
1. Click **Merchants** from the left-hand menu or click the **Merchants Full List** button from the dashboard to view all merchants.
1. Click **Become** to access the selected merchant's configurations:
<img src="images/console_mrchbecome.png">
1. Once you have "Become" the merchant you may manage the selected merchant's:
   * API configuration
   * Webhooks
   * PKI Management

## Retrieving the Merchant Identifier

To retrieve a merchant's unique identifier:
1. List the merchants.
1. The `Organisation Id` column in the list view is the unique merchant identifier.
1. Use this as the `encodedOrganisationId` identifier when requesting an [Access Token](http://localhost:4000/tok_reqtokorg.html#request-an-access-token-for-an-organisation) on behalf of your merchant(s).

{% include links.html %}
