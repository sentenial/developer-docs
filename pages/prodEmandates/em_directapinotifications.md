---
title: Managing Notifications
keywords: Managing Notifications
summary: "One or more E-Mail notifications are passed to your customers. This section describes how to manage these notifications."
sidebar: em_sidebar
permalink: em_directapinotifications.html
folder: prodEmandates
---

Your customers can receive two e-mail notifications as part of the E-Mandate signup flow:

* A message with a 4-digit code required to sign an e-mandate (if `E-Mail` is the selected authentication method).
* A confirmation e-mail, which is issued after signing, which includes a link to download a PDF copy of the mandate/DDI.

## E-Mail Authentication Setup

There are three basic Authentication Methods possible in E-Mandates:

* `Check Box`
* `E-mail`
* `SMS`

See the [E-Mandate Configurations](em_configuration.html#configurations) section for more on this.

If you have opted for `E-Mail` as your `Authentication Method`:

* Once users confirm their details and click OK on your UI to complete the signup flow, you will need to request them to provide a Confirmation Code to sign.
* In parallel, an email is issued to users with a 4-digit code.
* To sign the mandate, users need to take that 4-digit code, received via email, and type it in the Confirmation Code box on your Mandate Setup page.

To configure the E-mail links that are used, see the [Configuration API](em_applyconfig.html) section.
You will need to set the following values:

* `email Domain`
* `emailUrl`

{% include note.html content="If you do not configure these values, your emails will be issued from the Nuapay domain by default." type="primary" %}



{% include links.html %}
