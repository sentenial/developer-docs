---
title: Outbound Instant Payments Overview
keywords: Outbound Instant Payments Overview
summary: "Outbound Instant Payment processing"
sidebar: ip_sidebar
permalink: ip_outboundoverview.html
folder: prodInstantPayments
---

The Origix Instant Payments solution provides the following RESTful APIs:

* createInstPayment
* retrieveInstPayment

When your client creates an instant payment it goes through the following stages (where the payment is successfully processed):


## The Initial Originator Request

The initial outgoing payment is created by the payment originator, passed to the client's bank and on to Origix IP.

<img src = "images/sipFlow1.png">

Click the tabs for more details on each stage:

<ul id="profileTabs" class="nav nav-tabs">
    <li class="active">
        <a href="#Originator" data-toggle="tab">Originator</a></li>
    <li><a href="#Bank" data-toggle="tab">Bank</a></li>
    <li><a href="#OrigixIP" data-toggle="tab">Origix IP</a></li>
</ul>
  <div class="tab-content">
<div role="tabpanel" class="tab-pane active" id="Originator">
    <b>Originator</b>
<p>To begin:</p>
<ul>
<li>The originator (i.e. the PSP's client) wants to make a payment. </li>
<li>The user Initiates an SCT Inst instruction, via a client application for example.</li>
</ul>
</div>

<div role="tabpanel" class="tab-pane" id="Bank">
    <b>Bank / PSP</b>
    <p>Based on the client's request:</p>
    <ul>
    <li>The PSP's system initiates the <b>Create Instant Payment</b> API REST request.</li> 
    <li>The request is forwarded to Origix IP to create the payment.</li>
    </ul>
    </div>

<div role="tabpanel" class="tab-pane" id="OrigixIP">
    <b>Origix IP</b>
    <p>The Origix IP system then:</p>
    <ul>
    <li>Processes the API request.</li>
    <li>Validates the payment (for example, is the payee's Bank a participant in the SCT Inst scheme?)</li>
    <li>Creates the Instant Payment, ready to be passed on to the CSM.</li>
    <li>Generates a REST response back to the PSP's calling application, indicating that the payment has been submitted to the CSM and is in Pending status.</li>
    </ul>
</div>
</div>

<br/>
{% include note.html content="A successful response to the Create Instant Payment REST request is a 201 Created; note that the payment is not complete at this point. No funds are transferred and the payment is generated in a Pending status." %}

## Handling the Beneficiary Response

Origix IP passes the request on to the CSM from where it is forwarded to the beneficiary's bank.

<img src="images/sipFlow2.png">

Click the tabs for more details on each stage:

<ul id="profileTabs" class="nav nav-tabs">
    <li class="active">
        <a href="#OrigixIP2" data-toggle="tab">Origix IP</a></li>
    <li><a href="#RT1" data-toggle="tab">RT1</a></li>
    <li><a href="#BeneBank" data-toggle="tab">Beneficiary Bank</a></li>
</ul>
  <div class="tab-content">
<div role="tabpanel" class="tab-pane active" id="OrigixIP2">
    <b>Origix IP</b>
    <br/>Once the payment is created in Origix IP:
    <ul>
    <li>A timestamp is added to the SCT Inst message.</li> 
    <li>It is transmitted to the CSM (RT1).</li>
    <li>The CSM will forward the message details to the beneficiary bank and pass back a confirmation message.</li>
    </ul>
</div>

<div role="tabpanel" class="tab-pane" id="RT1">
    <b>RT1</b>
    <p>The CSM (RT1) receives the message from Origix IP and manages:</p>
    <ul>
    <li>SCT Inst Message validation.</li>
    <li>Time-stamp-checking: the time stamp applied by Origix IP prior to submission is validated (this must be within the scheme-specific timeout deadline of 20 seconds).</li>
    <li>The routing of the SCT Inst message to the Beneficiary Bank.</li>
    <li>The confirmation message (positive or negative) from the Beneficiary Bank.</li>
    <li>The forwarding of the Beneficiary Bank's confirmation message to Origix IP.</li>
    </ul>
    
    
    </div>

<div role="tabpanel" class="tab-pane" id="BeneBank">
    <b>Beneficiary Bank</b>
    <br/>The payee's bank:
    
    <ul>
    <li>Receives the SCT Instant message from RT1.</li>
    <li>Responds to RT1 with a confirmation message (positive or negative)</li>    
    </ul>
</div>
</div>

Test



{% include links.html %}
