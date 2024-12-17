---
title: Self-Hosted - Payment & E-Mandate Setup Flow
keywords: Self Hosted Payment & E-Mandate Setup Flow
summary: "For Partners/Merchants who would like to use the payment & E-Mandate setup flow, using their own User Interface, this section describes the APIs required."
sidebar: em_sidebar
permalink: em_obpsselfhosted.html
folder: prodEmandates
---

In order to launch the Open Banking Payment and E-Mandate signup flow, in `SELF_HOSTED` mode, you must call a number of payment- and mandate-related APIs, as outlined below.

|<img src="images/postman-logo.png">|<br>We highly recommend that you use **Postman** to test our APIs on the Sandbox environment. See the <a href = 'prod_postmoverview.html'>Postman Overview</a> section for more on this.<br>|

## Payment APIs

The following APIs are required:


<table style="width: 100%">
  <tbody>
    <tr>
      <td><strong>Service</strong></td>
      <td><strong>Endpoint</strong></td>
      <td><strong>Description</strong></td>      
    </tr>
    <tr>
    <td><a href= "ob_getbank.html">Retrieve Bank</a></td>
      <td>GET /banks</td>
      <td>Returns the list of banks to be displayed on the Bank Selection screen.</td>      
    </tr>
    <tr>
    <td><a href= "ob_createpayment.html">Create Payment</a></td>
      <td>POST /payments</td>
      <td>Creates the Open Banking payment.As part of this interaction the payer is:
      <uL>
      <li>Passed to the selected bank to authorise the payment.</li>
      <li>Redirected back from the bank.</li>
      </uL>
      </td>
    </tr>
    <tr>
    <td><a href= "ob_retrievepayment.html">Retrieve Payment</a></td>
      <td>GET / payments/{paymentId}</td>
      <td>Retrieve the Payment Details to check its status = <code class="highlighter-rouge">PAYMENT_RECEIVED</code> or wait for the <code class="highlighter-rouge">PaymentReceived</code> Webhook (or both).
      <br/>
      This call also retrieves the debtor details for the E-Mandate preparation step.</td>      
    </tr>

  </tbody>
</table>


## Create & Sign the Mandate/DDI

Once the payment has been successfully processed, the following services are required to complete the E-Mandate signing step:


<table style="width: 100%">
  <tbody>
    <tr>
      <td><strong>Service</strong></td>
      <td><strong>Endpoint</strong></td>
      <td><strong>Description</strong></td>      
    </tr>
    <tr>
    <td><a href= "em_prepare.html">Prepare E-Mandate</a></td>
      <td>POST /emandates</td>
      <td>This request returns a unique token used to render the E-Mandate screen. The Token encapsulates:
        <ul>
        <li>The Merchant configurations</li>
        <li>Merchant-specific details (Creditor Scheme ID, Scheme Type, etc.)</li>
        <li>Payer details (Address details, phone details, email, etc.)</li>
        </ul>
        The account details retrieved from the Open Banking payment are used to pre-populate the account details when the PSU goes to sign the E-Mandates. Note that these details are displayed in read-only mode, the user cannot modify the details.
        </td>      
    </tr>
    <tr>
    <td><a href= "em_init.html">Initialise Conversation</a> (Optional)
</td>
      <td>GET /conversations/init</td>
      <td>Call this service to see the next available steps in the conversation.
      <br/>This is an optional step.
        </td>      
    </tr>
      <tr>
    <td><a href= "em_sign.html#get-conversationsign">Retrieve E-Mandate Details</a> (Optional)
</td>
      <td>GET /conversations/sign</td>
      <td>Use this service to retrieve the E-Mandate details to be rendered for the payer to sign.
      <br/>This is an optional step.
        </td>      
    </tr>
     <tr>
    <td><a href= "em_sign.html#post-conversationsign">Sign Mandate</a>
</td>
      <td>POST /conversations/sign</td>
      <td>Call this service to sign the Mandate. This step is required. Certain response elements should be stored for use later.
      <ul>
      <li>The encodedMandateId and encodedSchemeId are required to build the URI where you can retrieve your Signed Mandate details. </li>
      <li>You will also need this for matching of the <code class="highlighter-rouge">MandateElectonicSign</code> notification (if you have enabled the <a href ="em_whmandsignature.html">Mandate Signature</a> Webhook.</li>
      </ul>     
        </td>      
    </tr>
     <tr>
    <td><a href= "em_retrieve_doc.html">Retrieve E-Mandate</a> (Optional)
</td>
      <td>GET /conversations/document</td>
      <td>After the E-Mandate is signed the PSU may receive a Mandate PDF via E-Mail. If you want to download the PDF for your records use this service.
      <br/>This step is optional     
        </td>      
    </tr>
     <tr>
    <td><a href= "np_retrievemandate.html">Retrieve Mandate</a> (Optional)
</td>
      <td>GET /schemes/{schemeId}/mandates/{mandateId}</td>
      <td>Use this service to retrieve the mandate details after it has been signed.
      <br/>This step is optional     
        </td>      
    </tr>

  </tbody>
</table>
