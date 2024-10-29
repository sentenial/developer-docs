---
title: E-Mandate Configuration
keywords: E-Mandate Configuration Config Emandate Setup
summary: "Various configurations and customisations are available when setting up your E-Mandates solution."
sidebar: em_sidebar
permalink: em_configuration.html
folder: prodEmandates
---

{% include important.html content="Specific configurations are generally carried out internally by Nuapay staff so please discuss your requirements with a member of our Customer Support team who will be able to assist you in this. Alternatively, you may make your own configuration changes via the Configuration API." %}

The E-Mandate application can be customised to enhance your clients' experience and align with your branding requirements.

It's possible to customise various settings in the following areas:

* User Interface
* Authorisation/Security
* Communication


<img src='images/em_config_overview.png'>

## UI Settings

|**Setting Name**| **Values**| **Description**|
|Logo URL| User-Defined | A URL link to your corporate logo. This logo will be displayed on the E-Mandate UI and also included in any emails generated. |
|Primary Colour| A Hex value | This sets the colour of the buttons and spinner graphics on the E-mandate UI.|
|Border Colour| A Hex value | Allows you to specify the border colour in emails.|
|White Labelling| Yes/No| Allows you to control whether the Powered by Nuapay text is displayed in the E-Mandate footer.|
|Display Extended Data| Yes/No |Available for the SEPA scheme only. Depending on your business needs you may already have specific customer details (address details for example) and you may just want to collect your customer’s IBAN. This setting allows you to just present a slimmed down set of input fields. If set to No, only Account Holder Name, IBAN and Email are displayed.  |
|Debtor Input Allowed| Yes/No |When set to Yes, your customer can modify the fields on the E-Mandate application. |
|Hide Address Field| Yes/No |If set to true, the address fields are not displayed.|
|Hide Mobile Number Field| Yes/No |If set to true, the Mobile Number is not displayed.|
|Hide Contract Reference Field| Yes/No |If set to true, the Mobile Number is not displayed.|
|Show Confirmation Screen| Yes/No |Allows you to control whether the Confirmation page is displayed or if the user is passed to the Success/Failure URL directly. |
|Success & Failure URLs| User-defined |These are static pages that allows you to control the URL on which your customer finished the signup flow.|

## Authorisation & Security Settings

|**Setting Name**|**Values**|**Description**|
|Authentication|`None`, `AISP`| If set to `None`, the standard E-Mandate flow is used. If set to `AISP`, your customers are redirected to their bank to confirm that they are the account owners: see the [AIS Signup Flow](em_obaslaunching.html) for more on this.|
|Authorization|`Check box`, `SMS Password`, `Email Password`| The method required to sign an e-mandate. `Check box` is the simplest: the user selects the option to confirm. In `Email` and `SMS`, a 4-digit code is passed to the user via one of those channels, which must be used to confirm the mandate setup. |
|PDF Certification| `Uncertified`, `Morpho`| For added security, PDF mandates may be signed and stored via a third-party, Morpho.|
|E-mandate Expiry (Days)| A numeric value | The default is set to 30. If a user attempts to sign an e-mandate after this configured number of days an error message is displayed.|

## Communication Settings

|**Setting Name**| **Values**| **Description**|
|Debtor Communication| `None`, `Email`| Allows you to manage whether emails are issued to your customers on signing, activation, etc.|
|Creditor Confirmation Email| Any email address| Provide your email address here if you, as the merchant, want to be notified when a payer signs an emandate.|


For more details on these customisations, and examples, see [E-Mandate Customisations](em_uicustomisations.html).


{% include note.html content="For Bacs E-mandates the Bacs DD Guarantee and logo are populated by default." %}


{% include links.html %}
