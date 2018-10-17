---
title: Inbound Instant Payments Overview
keywords: Inbound Instant Payments Overview
summary: "Inbound Instant Payment processing"
sidebar: ip_sidebar
permalink: ip_inboundoverview.html
folder: prodInstantPayments
---

When processing inbound payments:

* Any Instant Payments where the beneficiary account details referenced in the payment refers to your Financial Institution's / PSPS's BIC will be routed from the CSM to Origix IP.
* Origix IP will perform message and business validations and extract the payee's account triggering a request to your Financial Institution's / PSP's configured Validate Account endpoint.
* Upon successful account validation, Origix IP will transmit a confirmation message to the CSM
* The CSM will respond with a formal notification of the SCT Inst instruction status.
* A Webhook confirmation message is passed to the Beneficiary Bank confirming the final status of the payment.

The steps involved in an inbound payment flow are detailed below:

## External Originator to CSM and to Origix IP

The incoming payment is transmitted to Clearing (RT1, for example) and on to Origix IP.

<img src = "images/sipFlowIn1.png">

Click the tabs for more details on each stage:

<ul id="profileTabs" class="nav nav-tabs">
    <li class="active">
        <a href="#ExtOriginator" data-toggle="tab">External Originator</a></li>
    <li><a href="#Clearing" data-toggle="tab">Clearing</a></li>
    <li><a href="#OrigixIP" data-toggle="tab">Origix IP</a></li>
</ul>
  <div class="tab-content">
<div role="tabpanel" class="tab-pane active" id="ExtOriginator">
    <b>External Originator</b>
<p>The Originator of the payment (This is the party paying into your client's account):</p>
<ul>
<li>Generates an SCT Inst instruction.</li>
<li>The payment is passed to the CSM.</li>
</ul>
</div>

<div role="tabpanel" class="tab-pane" id="Clearing">
    <b>Clearing</b>
    <p>The CSM:</p>
    <ul>
    <li>Processes the Inbound SCT Inst instruction.</li> 
    <li>Performs validations and determines the beneficiary BIC (this is the Bank's BIC)</li>
    <li>Routes the payment to Origix IP.</li>
    </ul>
    </div>

<div role="tabpanel" class="tab-pane" id="OrigixIP">
    <b>Origix IP</b>
    <p>The Origix IP system:</p>
    <ul>
    <li>Processes the incoming payment.</li>
    <li>Determines the Beneficiary Bank that will need to be credited.</li>
    <li>Performs validations (see below) </li>
    </ul>
</div>
</div>

## Origix IP to Beneficiary Bank

Origix IP will match the payment to the approriate BIC and account.

<img src="images/sipFlowIn2.png">

Click the tabs for more details on each stage:

<ul id="profileTabs" class="nav nav-tabs">
    <li class="active">
        <a href="#OrigixIP2" data-toggle="tab">Origix IP</a></li>   
    <li><a href="#BeneBank" data-toggle="tab">Beneficiary Bank</a></li>
</ul>
  <div class="tab-content">
<div role="tabpanel" class="tab-pane active" id="OrigixIP2">
    <b>Origix IP</b>
   The Origix IP application:
    <ul>
    <li>Extracts the account provided in the payment.</li> 
    <li>Initiates a REST request to the appropriate client Bank's configured Account Validation Endpoint.</li>
    
    </ul>
</div>

<div role="tabpanel" class="tab-pane" id="BeneBank">
    <b>Beneficiary Bank</b>
    <br/>The receiving bank:
    
    <ul>
    <li>Consumes the Validate Account REST request from Origix IP.</li>
    <li>Determines if the account is valid (validation may fail where an account is closed or where an account owner is deceased, for example).</li>
    <li>Responds (via REST) to the request with a positive or negative validation result.</li>
    </ul>
</div>
</div>

## Origix IP Responds to the CSM

Based on the Beneficiary bank's response, Origix IP will respond to the CSM.


<img src="images/sipFlowIn3.png">

Click the tabs for more details on each stage:

<ul id="profileTabs" class="nav nav-tabs">
    <li class="active">
        <a href="#OrigixIP3" data-toggle="tab">Origix IP</a></li>
    <li><a href="#Clearing2" data-toggle="tab">Clearing</a></li>
    
</ul>
  <div class="tab-content">
<div role="tabpanel" class="tab-pane active" id="OrigixIP3">
    <b>Origix IP</b>
    <br/>Having processed the response from the Beneficiary Bank, Origix IP:
    <ul>
    <li>Consumes the Validate Account REST response from the client Financial Institutions / PSPS.</li> 
    <li>Responds to the CSM with a positive / negative confirmation.</li>     
    </ul>
</div>

<div role="tabpanel" class="tab-pane" id="Clearing2">
    <b>Clearing</b>
    <p>The CSM:</p>
    <ul>
    <li>Processes the confirmation message from Origix IP.</li>
    <li>Forwards the confirmation message to the originating bank.</li>    
    <li>Dispatches a formal notification message in response to Origix IP.</li>
    </ul>
    
    
    </div>


</div>

## Origix IP Notification to the Beneficiary Bank

For the final stage in the incoming payment flow Origix IP will notify the Beneficiary Bank of the final status of the payment, based on the final response from the CSM.


<img src="images/sipFlowIn3.png">

Click the tabs for more details on each stage:

<ul id="profileTabs" class="nav nav-tabs">
    <li class="active">
        <a href="#OrigixIP4" data-toggle="tab">Origix IP</a></li>
    <li><a href="#BeneBank4" data-toggle="tab">Clearing</a></li>
    
</ul>
  <div class="tab-content">
<div role="tabpanel" class="tab-pane active" id="OrigixIP4">
    <b>Origix IP</b>
    <br/>To notify the Beneficiary Bank of the final status, Origix IP:
    <ul>
    <li>Processes the formal notification response from the CSM.</li> 
    <li>Generates and transmits a Webhook message.</li> 
    <li>The message will indicate the settlement of the instruction at the CSM (Incoming Accept, for example) or may indicate if the payment has failed. </li>     
    </ul>
</div>

<div role="tabpanel" class="tab-pane" id="BeneBank4">
    <b>Beneficiary Bank</b>
    <p>The Bank will:</p>
    <ul>
    <li>Receive the Webhook notification.</li>
    <li>Credit the funds to the beneficiary's account, assuming a positive Webhook has been received.</li>    
    
    </ul>
    
    
    </div>


</div>



{% include links.html %}
