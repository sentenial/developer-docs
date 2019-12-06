---
title: Email Customisation
keywords: Customising Email Communications, SPF
summary: "This section outlines how to configure E-Mandates (and your DNS settings) so that the automatically-generated E-Mandate emails appear to be originating from YOUR domain."
sidebar: em_sidebar
permalink: em_communications.html
folder: prodEmandates
---

Emails that are automatically generated and dispatched to your customers use the Sentenial domain: so (by default) your users will receive request-to-sign or confirmation emails from the sender address `emandates@sentenial.com`. 

As this may be confusing for users, who will generally not be aware that Sentenial are providing your business with Direct Debit payment services, it is possible to configure the sender addresses on these notifications to use your own business domain. 

So for a business called Merchant123, for example, the E-Mandates aplication may be configured so that all emails will have the sender address **emandates@Merchant123.com**.

In order to set this up some configurations are required:

* In the E-Mandates application.
* On your business's DNS Provider.

## E-Mandate Configurations

To have you domain name applied to the emails generated from the E-Mandates application: 

* Please contact a member of our support staff (click the Feedback link at the top of the page). 
* Once we have the details of the domain you want to use, we will make the necessary configuration updates for your organisation on our application.

We will notify you when the update has been completed.

## Adding Sentenial to Your SPF Record 

Once we have recorded your domain on our application, your technical operations staff will need to make an update on your business's DNS Provider configuration. 

Your DNS Provider will need to include Sentenial as a trusted domain. 

To do this: 

* Locate the Sender Policy Framework (SPF) record on your DNS Provider dashboard.
* Make an update to your SPF record to add `sentenial.com`

The following is a sample SPF record (where the business name is Merchant123.com). Note that `sentenial.com` has been added:

````js

id 43465
opcode QUERY
rcode NOERROR
flags QR RD RA
;QUESTION
Merchant123.com. IN TXT
;ANSWER
Merchant123.com. 299 IN TXT "v=spf1 mx ip4:123.456.789.12 mx:mail. merchant123.com a:webserver1.bizspacehost.com include:spf.protection.sentenial.com -all"
;AUTHORITY
;ADDITIONAL

````

{% include note.html content="It is important to ensure that the domain name you provide to the Nuapay support team and the domain name that you specify in the SPF record are identical; if there is a mismatch your domain name will not be used and emails will be dispatched with the default domain name." %}







{% include links.html %}
