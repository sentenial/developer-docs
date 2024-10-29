---
title: MTLS Configuration via REST
keywords: MTLS Configuration via REST
summary: "MTLS Configuration via REST"
sidebar: sec_sidebar
permalink: np_secmtlsrest.html
folder: prodSecurity
---

{% include tip.html content="It is possible to set up and manage MTLS via REST (as described in this section) or alternatively, this may be done via the [Nuapay User Interface](np_secmtlsui.html) through the Nuapay Console." %}

## Uploading an MTLS Certificate

To upload an MTLS certificate via REST:

* Call the `POST /certificates` endpoint ([Create Certificate](np_seccreatecert.html))
* In the body of the request, you must provide your `mtlsCert`.

Note that you must provide:
* A valid PEM certificate.
* It must be active (cannot br expired).
* Only the `mtlsCert` can be passed in the request (your request will be rejected if you pass a `csr` simultaneously).
* By default you may have up to two active MTLS certificates. (Having two active certifcates is useful where a certificate is due to expire).
