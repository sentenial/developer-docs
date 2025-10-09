---
title: CoP/VoP Test Data
keywords: CoP/VoP Test Data Stub
summary: "Use the provided names in the table below to call our Stub and simulate the various possible responses for your CoP/VoP checks on our Sandbox environment."
sidebar: ver_sidebar
permalink: ver_coptest.html
folder: prodNuapay
toc: false
---
## Overview

When testing the `ACCOUNT_HOLDER_VERIFICATION` APIs, it is possible to use the following test data to simulated specific results:

| Entity                  | Account Responded Name | Account Status | Account Name Check Status | Scheme Response Code |
|-------------------------|------------------------|----------------|---------------------------|----------------------|
| Acme Corporation        | Apex Corp.             | Active         | `NO_MATCH`                | ANNM                 |
| Beta Industries         | Brite Manufacturing    | Active         | `PARTIAL_MATCH`           | MBAM                 |
| Gamma Enterprises       | Glimmer Enterprise     | Active         | `PARTIAL_MATCH`           | BANM                 |
| Delta Limited           | Dusk Ltd.              | Active         | `PARTIAL_MATCH`           | PANM                 |
| Epsilon Innovations     | Enigma Innovate        | Active         | `PARTIAL_MATCH`           | BAMM                 |
| Zeta Solutions          | Zenith Solvers         | Active         | `PARTIAL_MATCH`           | PAMM                 |
| Omega Technologies      | -                      | Unknown        | `UNABLE_TO_MATCH`         | AC01                 |
| Neptune Systems         | -                      | Unknown        | `UNABLE_TO_MATCH`         | IVCR                 |
| Pluto Enterprises       | -                      | Unknown        | `UNABLE_TO_MATCH`         | ACNS                 |
| Saturn Solutions        | -                      | Forbidden      | `UNABLE_TO_MATCH`         | OPTO                 |
| Jupiter Innovations     | -                      | Unknown        | `UNABLE_TO_MATCH`         | CASS                 |
| Mars Corporation        | Meteor Corp.           | Unknown        | `UNABLE_TO_MATCH`         | SCNS                 |
| Eta Corporation         | -                      | Inactive       | `UNABLE_TO_MATCH`         | -                    |
| Theta Corporation       | -                      | Closed         | `UNABLE_TO_MATCH`         | -                    |


{% include note.html content="Any other name that is provided will result in a `FULL MATCH`" %}

## Response Codes

The following response codes are possible:

| **Status**           | **Code** | **Description**                                    |
|----------------------|----------|----------------------------------------------------|
| No Match             |          |                                                    |
|                      | ANNM     | Account Name does Not Match                        |
| Partial Match        | MBAM     | There may be a match on the Account Name          |
|                      | BANM     | Business account, name matches                     |
|                      | PANM     | Personal account, name matches                     |
|                      | BAMM     | Business account, name may be a match             |
|                      | PAMM     | Personal account, name may be a match             |
| Unable to Match      | AC01     | Incorrect Account Number                            |
|                      | IVCR     | Invalid Customer Reference                          |
|                      | ACNS     | Account type Not Supported for CoP                 |
|                      | OPTO     | Opted out of CoP Service                           |
|                      | CASS     | Account has been switched                          |
|                      | SCNS     | Sort code not supported at endpoint                |

