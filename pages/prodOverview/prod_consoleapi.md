---
title: Nuapay Console API Settings
keywords: Nuapay Console API Settings
summary: "Manage API keys and Whitelist IP addresses."
sidebar: productOverview_sidebar
permalink: prod_consoleapi.html
folder: prodOverview
---

As described in the [General API Rules](prod_generalrules.html) section, you must have an API key before you can interact with Nuapay and this section outlines how you can set up your API Key when acting as a <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.merchant}}">Merchant</a> or as a <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.partner}}">Partner</a>.

## API Key Configuration

{% include note.html content="The following screens relate to a merchant but the steps are identical for partner users." %}
Once you've successfully logged on to the Console you will first need to create your API Key:

1. Click the **Generate new API Key** button from the home screen (or click this button when you select **API Configuration** from the left-hand menu):
<img src = "images/console_apikey.png">
1. This will generate your key, along with an option to copy it to the clipboard.
1. It is possible to generate a new key later, if required.

{% include warning.html content="Changing your API key will require an update to your API setup so exercise extreme care before making any change. Once you generate a new API key the previous key CANNOT be restored!" %}

## Allowed-IPs Configuration

Once you have created your API Key, you will need to configure your <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.allowed-ips}}">Allowed IP addresses</a>:

1. Click **API Configuration** from the left-side menu.
1. Select the Access Config tab:
<img src = "images/console_accessconfig.png">
1. Click the **Edit** button.
1. Type the IP address(es) that you want to Whitelist.
1. Where you specify more than one IP address, each must be separated by a semicolon (;), for example `12.345.678.90;23.456.78.90;123.456.7.8`


{% include links.html %}
