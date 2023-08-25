---
title: AIS Self-Hosted Payment Page Setup
keywords: AIS Self Hosted Consent Request Page Setup
summary: "Adding Open Banking (Self-Hosted mode) as an account access option requires configuration as outlined below. In Self-Hosted mode you must develop your own user interface."
sidebar: ob_sidebar
permalink: ob_aisselfsetupoverview.html
folder: prodOpenBanking
toc: false
---

## Overview

The following image outlines the sequence of API call required to create a consent and use it to retrieve account details (in the `SELF-HOSTED` integration):

{% include image.html file="ob_selfhost_ais_flow.png" url="images/ob_selfhost_ais_flow.png" target = "_new" alt="AIS Self-Hosted Flow" caption="AIS SELF_HOSTED Partner Flow" %}

All the endpoints referenced in the image above are described in the Account Information API section.

1. Partner users will need to first retrieve the required `merchantId`. The customer of this merchant is the subject of the consent request being made.
1. Retrieve the bank list to be displayed to the end user. The user will select the required bank.
1. With a selected bank, create the Consent request and return the redirect URL to the user.
1. The user follows the redirect and provides authorisation for the access request at the selected ASPSP; following this the user is redirected to the `postAuthURL`. 
1. The consent status request can be retried until an `ACTIVE` status is returned.

With an `ACTIVE` consent, it is then possible to initiate an account access request.
## Merchant Post-Auth URL Handling
  {% include self_hosted_shared.html %}
