---
title: Webhooks Overview
keywords: Webhooks Overview Instant Payments
summary: "Webhooks can be used to notify your internal systems when specific Instant Payment events occur."
sidebar: ip_sidebar
permalink: ip_whoverview.html
folder: prodInstantPayments
---


Webhooks are HTTP notifications, dispatched to a specified URL (configured by your Financial Institution / PSP) when certain events are triggered in Origix IP. Unlike an API request, where your systems initiate a request and waits for a response, with Webhooks your configured Endpoint will automatically receive a notification (similar to an API response) when certain events occur.

For more information on the setup and configuration of Webhooks, see the general [Webhooks section](wh_overview.html) (under the Products menu). 

The following events are currently supported:

* Outbound Payments
  - [Accepted Payment](ip_whoutaccept.html)
  - [Rejected Payment](ip_whoutreject.html)
* Inbound Payments
  - [Accepted Payment](ip_whinaccept.html)
  - [Rejected Payment](ip_whinreject.html)