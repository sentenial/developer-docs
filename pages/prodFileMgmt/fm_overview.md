---
title: File Management Overview
keywords: File Management APIs Overview
summary: "File Management APIs allow you to use various endpoints to manage Direct Debit and Credit Transfer payment files via REST."
sidebar: fm_sidebar
permalink: fm_overview.html
folder: prodFileMgmt
---

Nuapay allows users to process Direct Debit and Credit Transfer transactions via three channels:

* User Interface (UI).
* File.
* REST API.

Using the Nuapay File Management APIs, it is possible to upload files to the Nuapay File Processing location via the [File Upload](fm_file_upload.html) service.

## General Overview

`Files` are composed of:

* `Batches`; a batch is a collection of transactions. A single file may have 1-n batches within it.
* `Transactions`; there are 1-n transactions within a batch.

See [Supported File Types](fm_supported_filetypes.html) for information on the Direct Debit and Credit Transfer files that may be embedded in the upload API.
