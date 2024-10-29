---
title: MTLS UI Setup
keywords: MTL Configuration via the UI
summary: "MTLS User Interface Configuration"
sidebar: sec_sidebar
permalink: np_secmtlsui.html
folder: prodSecurity
---

It is possible to set up and manage the MTLS via the User Interface (as described in this section) or alternatively, this may be done via [REST](np_secmtlsrest.html).

## Uploading a Certificate via the UI

{% include note.html content="You will require access to the Nuapay Console to configure your MTLS settings via the User Interface. See the [Nuapay Console Overview](prod_consoleoverview.html) for more details." %}

To upload your certificate:

1. Navigate to the **PKI Management** screen on the Nuapay Console. (If you cannot see this as a menu option please contact your Account Manager - specific permissions must be enabled to allow you to access this section of the dashboard).
1. Click <b>Upload MTLS Certificate</b>:
 	 <img src ='images/sec_uploadmtlscert.png'>
1. Paste your certificate into the text box area:
	 <img src = 'images/sec_mtlscert.png'>
1. Click **Upload MTLS Certificate**.

## Access Configuration

Once you have uploaded your certificate:
1. Browse to **API Configuration** (left-hand menu).
1. Select the **Access Config** tab.
1. Click **Edit**
1. Select the **MTLS** check box:
	 <img src = 'images/sec_mtlschkbx.png'>
1. Click **Save**.

## Additional Notes on MTLS

Note that:

* You can upload any certificate for MTLS [self signed certificates are permitted] i.e., you do not have to use Nuapay’s `POST /certificates` endpoint.
* MTLS-enabled clients should call Nuapay APIs on Port 8443.
* You may register more than one client certificate. This is useful as it allows you to rotate certificates and allows you to avoid any potential downtime due to certificate expiry, for example.
