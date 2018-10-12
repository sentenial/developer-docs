---
title: Redirect Success and Failure
keywords: E-Mandate Redirect Handling Redirect Success and Failure
summary: "Handling the rendering of the Success and Failure Page."
sidebar: em_sidebar
permalink: em_redirecteventhandler.html
folder: prodEmandates
---

Depending on how your business has been configured on the E-Mandates platform, when your payers click the Sign button they may be directed to provide an authentication code. This unique code will be sent to your payers either via SMS or e-mail.

{% include note.html content="You will need to provide our configuration team with the Success and Failure URLs that you require when you first register for E-Mandates. See the  [Configuration section](em_configuration.html)." %}

Once the payer has verified his/her details and a success page has been returned you will need to persist the following details returned in the Success URL:

* Encoded mandate ID
* Encoded scheme ID
* Optionally the (unencoded) mandate reference (or UMR)


(You will use these values later to <a href="np_createdirectdebit.html">Create Direct Debit</a> payments).


The **Success Page** URL might have the following query parameters, for example:

````
?encodedmandateid=ym3nexy9lb&encodedschemeid=8b5gxgrz2r&mandateid=ABC004159108810C&umr=ABC004159108810C&token=cfe979a1-edb5-47df-8511-b92d700c0e0b
````


A **Failure Page** URL would have the following, for example:

````
?cancel=true&errorcode=null&token=e27ae877-8c51-464a-928b-ffbce5a667e9
````

{% include links.html %}
