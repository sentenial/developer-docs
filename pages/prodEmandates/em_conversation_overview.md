---
title: Coversation API Overview
keywords: E-Mandate Conversation Steps
summary: "When building a direct API integration, conversation steps can be useful to allow you to further customise your integration"
sidebar: em_sidebar
permalink: em_conversation_overview.html
folder: prodEmandates
---

To provide you with greater control over the Direct API Integration, use our API conversation steps when building your solution.
The following conversation steps are available (with links to the Swagger definitions for each service):

|**Method**|**Service**|**URI**|
|<span class="label label-success">GET</span>| Settings | [/conversations/settings](https://sentenial.github.io/emandates-swagger/docs/redoc.html#operation/settingsGetUsingGET)|
|<span class="label label-success">GET</span>| Initialise Conversation | [/conversations/init](https://sentenial.github.io/emandates-swagger/docs/redoc.html#operation/initGetUsingGET) |
|<span class="label label-success">GET</span>| Sign | [/conversations/sign](https://sentenial.github.io/emandates-swagger/docs/redoc.html#operation/signMandateGetUsingGET) |
|<span class="label label-info">POST</span>| Sign | [/conversations/sign](https://sentenial.github.io/emandates-swagger/docs/redoc.html#operation/signMandatePostUsingPOST) |
|<span class="label label-success">GET</span> | Verify | [/conversations/verify](https://sentenial.github.io/emandates-swagger/docs/redoc.html#operation/verifyGetUsingGET) |
|<span class="label label-info">POST</span>| Verify |  [/conversations/verify](https://sentenial.github.io/emandates-swagger/docs/redoc.html#operation/verifyPostUsingPOST) |
|<span class="label label-success">GET</span>| Resend One-Time Password | [/conversations/resend](https://sentenial.github.io/emandates-swagger/docs/redoc.html#operation/resendOtpPostUsingGET) |
|<span class="label label-info">POST</span>| Resend One-Time Password | [/conversations/resend](https://sentenial.github.io/emandates-swagger/docs/redoc.html#operation/resendOtpPostUsingPOST) |
|<span class="label label-success">GET</span>| Confirm| [/conversations/confirm](https://sentenial.github.io/emandates-swagger/docs/redoc.html#operation/confirmMandateGetUsingGET) |
|<span class="label label-info">POST</span>| Confirm| [/conversations/confirm](https://sentenial.github.io/emandates-swagger/docs/redoc.html#operation/confirmMandatePostUsingPOST) |
|<span class="label label-success">GET</span>| Document| [/conversations/{conversationToken}/document](https://sentenial.github.io/emandates-swagger/docs/redoc.html#operation/generatePdfGetUsingGET) |
|<span class="label label-success">GET</span>| Download Contract Document | [/conversations/contract](https://sentenial.github.io/emandates-swagger/docs/redoc.html#operation/conversationContractGetUsingGET)|


These services can be used when you need to implement a specific flow. 
The following implementations examples show how you can work with the conversation APIs to:

* [Set up SMS Authentication](em_conversation_settings.html)
* [Resend a One-Time-Password](em_conversation_resend_settings.html)
<!--* Contract Signing-->


{% include links.html %}
