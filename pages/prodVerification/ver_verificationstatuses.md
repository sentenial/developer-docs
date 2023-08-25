---
title: Verification Statuses
keywords: sample
summary: "A Verification check moves through various statuses in its lifecycle; these are described in this section."
sidebar: ver_sidebar
permalink: ver_verificationstatuses.html
folder: prodNuapay
---


## Overview

{% include callout.html content="Successfully processed Verification requests move through the following statuses: PENDING --> IN_PROGRESS --> COMPLETE or FAILED" type="primary" %}

## Verification Statuses

| Status | Description |
|-------|--------|
|`PENDING` | The `POST /verifications` request has been completed and the verification object has been created. The user has not yet provided consent at the bank.|
| `IN_PROGRESS` | The user has provided consent and the `PATCH /verifications/{verificationId}` has been called (the verification is in progress).|
| `COMPLETE`	 | The user has completed the verification check; consent has been provided and the verification has completed. |
| `FAILED`  | The consent was not retrieved or there has been some technical issue that resulted in the consent not being returned; the verification cannot be completed.  |


{% include links.html %}
