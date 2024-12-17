---
title: Quick Start PISP Initiation
keywords: Open Banking Quick Start
summary: "Quick Start - Let's make an Open Banking payment!"
sidebar: ob_sidebar
permalink: ob_quickstart.html
folder: prodOpenBanking
---

## Overview

You can interact with Nuapay Open Banking PISP via one of the following integration models:

* REDIRECT
* SELF-HOSTED
* SELF-HOSTED-CALLBACK
* <p style="color: #d3d3d3;">CHECKOUT</p>

See [PISP Implementation Options](ob_pispimplementations.html) for more on these options.

Depending on the setup that best suits your business needs, the API calls that you need to make and how you process the responses vary.


## A Note on Authentication

When interacting with the Nuapay Endpoints you must be authenticated via one of the following:

* API Keys
* OAuth Tokens

For more details on this see the section on [API Key Authentication](np_secapikeyauth.html) or OAuth Tokens in the [Token Management](tok_tokenmgmt.html) section.


## Postman Collection

|<img src="images/postman-logo.png">|<br>We highly recommend that you use **Postman** to test our PISP APIs on the Sandbox environment. See the <a href = 'prod_postmoverview.html'>Postman Overview</a> section for more on this.<br>|


{% include tip.html content="Unlike the Swagger specification, the Postman Collection we've created allows you to work with the APIs directly in our Sandbox environment. While our Swagger file is a formal definition of our PISP service, which you can use to generate client libraries, the Postman Collection logically groups the services together so that you can see the business logic of why (and when) to call the various PISP endpoints."%}

## Redirect Mode

{% include note.html content="CHECKOUT and REDIRECT is only available for merchants who want to process GBP payments; if you want to process EUR transactions then you must go with either the SELF-HOSTED or SELF-HOSTED-CALLBACK integration."%}

If you are acting as a _partner_:
* You will need to retrieve your merchant's identifier.
* If you want to set up a payment for Merchant X but do not have the merchant identifier and need to query the `GET /organisations` service to retrieve it as a first step.

Call the following services in this order

<table>
  <tbody>
    <tr>
      <td><a href="tok_listorgs.html"><span class="label label-success">GET</span></a></td>
      <td><a href="tok_listorgs.html">Organisations</a></td>
      <td>
        (Optional - <em>For Partner users only</em>) Use this service to retrieve the list of organisations/merchants under you as the Partner entity.
        <ul>
          <li>Use your Partner-level API Key</li>
          <li>Store the required merchant identifier</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><a href="tok_reqtokorg.html"><span class="label label-info">POST</span></a></td>
      <td><a href="tok_reqtokorg.html">Access Token</a></td>
      <td>
        (Optional) For merchants, use this service to retrieve an OAuth token. <br>For partners:
        <ul>
          <li>Retrieve an OAuth token for your required merchant</li>
          <li>Pass your API Key and merchantId</li>
          <li>Set scope = <code>openbanking_pisp</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><a href="ob_createpayment.html#create-payment-endpoint"><span class="label label-info">POST</span></a></td>
      <td><a href="ob_createpayment.html#create-payment-endpoint">Create Payment</a></td>
      <td>        
        Note that:
        <ul>
          <li>The <code>integrationType</code> must be set to <strong>REDIRECT</strong></li>
          <li>The <code>merchantPostAuthUrl</code> must be provided</li>
          <li>The Create Payment service generates an Open Banking payment object</li>
          <li>Returns a unique <code>userInterfacePaymentId</code></li>
          <li>Initial payment status is <a href="ob_paymentstatuses.html"><strong>PENDING</strong></a></li>
          <li>The URI must be passed to the PSU</li>
          <li>Bank Selection screen launches in a new browser window/tab when the user clicks the link</li>
        </ul>          
      </td>
    </tr>
    <tr>
      <td>-</td>
      <td>-</td>
      <td>
        The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank and is redirected to authenticate and approve the payment on that <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP's</a> online banking portal.
      </td>
    </tr>
    <tr>
      <td><a href="ob_retrievepayment.html#retrieve-payment-endpoint"><span class="label label-success">GET</span></a></td>
      <td><a href="ob_retrievepayment.html#retrieve-payment-endpoint">Retrieve Payment Status</a></td>
      <td>
        Retrieve the status of the payment.
      </td>
    </tr>
  </tbody>
</table>


For more details on this see the [Redirect Setup](ob_redirectoverviewmerch.html).

## Self-Hosted

Call the following services in this order:

<table>
  <tbody>
    <tr>
      <td><a href="tok_listorgs.html"><span class="label label-success">GET</span></a></td>
      <td><a href="tok_listorgs.html">Organisations</a></td>
      <td>
        (Optional - <em>For Partner users only</em>) Use this service to retrieve the list of organisations/merchants under you as the Partner entity.
        <ul>
          <li>Use your Partner-level API Key</li>
          <li>Store the required merchant identifier</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><a href="tok_reqtokorg.html"><span class="label label-info">POST</span></a></td>
      <td><a href="tok_reqtokorg.html">Access Token</a></td>
      <td>
        (Optional) For merchants, use this service to retrieve an OAuth token. <br>For partners:
        <ul>
          <li>Retrieve an OAuth token for your required merchant</li>
          <li>Pass your API Key and merchantId</li>
          <li>Set scope = <code>openbanking_pisp</code></li>
        </ul>
      </td>
    </tr>
	<tr>      
	  <td><a href="ob_retrievepayment.html#retrieve-payment-endpoint"><span class="label label-success">GET</span></a></td>
      <td><a href="tok_reqtokorg.html">Retrieve Banks</a></td>
      <td>
        Use this service to give your <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> a list of banks from which to choose.
      </td>
    </tr>
	<tr>
      <td>-</td>
      <td>-</td>
      <td>
        The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>.
      </td>
    </tr>
    <tr>
      <td><a href="ob_createpayment.html#create-payment-endpoint"><span class="label label-info">POST</span></a></td>
      <td><a href="ob_createpayment.html#create-payment-endpoint">Create Payment</a></td>
      <td>        
        Once the user selects an ASPSP, pass its <code>bankId</code> in the payment request. Note that:
        <ul>
          <li>The <code>integrationType</code> must be set to <strong>SELF_HOSTED</strong></li>
          <li>The <code>merchantPostAuthUrl</code> must be provided</li>
          <li>The Create Payment service generates an Open Banking payment object</li>
          <li>Returns a unique <code>userInterfacePaymentId</code></li>
          <li>Initial payment status is <a href="ob_paymentstatuses.html"><strong>PENDING</strong></a></li>
          <li>The URI must be passed to the PSU</li>
          <li>Bank Selection screen launches in a new browser window/tab when the user clicks the link</li>
        </ul>          
      </td>
    </tr>
    <tr>
      <td>-</td>
      <td>-</td>
      <td>
        The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> is redirected to authenticate and approve the payment on that <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP's</a> online banking portal.
		 Once the user approves or declines the payment he/she is redirected to the <code>merchantPostAuthUrl</code> (as referenced in the Create Payment call).
      </td>
    </tr>
    <tr>
      <td><a href="ob_retrievepayment.html#retrieve-payment-endpoint"><span class="label label-success">GET</span></a></td>
      <td><a href="ob_retrievepayment.html#retrieve-payment-endpoint">Retrieve Payment Status</a></td>
      <td>
        Retrieve the status of the payment.
      </td>
    </tr>
  </tbody>
</table>


For more details on this see the [Self-Hosted Setup](ob_selfsetupoverviewmerch.html) section.

## Self-Hosted Callback

Call the following services in this order:


<table>
  <tbody>
    <tr>
      <td><a href="tok_listorgs.html"><span class="label label-success">GET</span></a></td>
      <td><a href="tok_listorgs.html">Organisations</a></td>
      <td>
        (Optional - <em>For Partner users only</em>) Use this service to retrieve the list of organisations/merchants under you as the Partner entity.
        <ul>
          <li>Use your Partner-level API Key</li>
          <li>Store the required merchant identifier</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><a href="tok_reqtokorg.html"><span class="label label-info">POST</span></a></td>
      <td><a href="tok_reqtokorg.html">Access Token</a></td>
      <td>
        (Optional) For merchants, use this service to retrieve an OAuth token. <br>For partners:
        <ul>
          <li>Retrieve an OAuth token for your required merchant</li>
          <li>Pass your API Key and merchantId</li>
          <li>Set scope = <code>openbanking_pisp</code></li>
        </ul>
      </td>
    </tr>
	<tr>      
	  <td><a href="ob_retrievepayment.html#retrieve-payment-endpoint"><span class="label label-success">GET</span></a></td>
      <td><a href="tok_reqtokorg.html">Retrieve Banks</a></td>
      <td>
        Use this service to give your <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> a list of banks from which to choose.
      </td>
    </tr>
	<tr>
      <td>-</td>
      <td>-</td>
      <td>
        The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects an <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>.
      </td>
    </tr>
    <tr>
      <td><a href="ob_createpayment.html#create-payment-endpoint"><span class="label label-info">POST</span></a></td>
      <td><a href="ob_createpayment.html#create-payment-endpoint">Create Payment</a></td>
      <td>        
        Once the user selects an ASPSP, pass its <code>bankId</code> in the payment request. Note that:
        <ul>
          <li>The <code>integrationType</code> must be set to <strong>SELF_HOSTED_CALLBACK</strong></li>
          <li>The <code>merchantPostAuthUrl</code> must be provided</li>
          <li>The Create Payment service generates an Open Banking payment object</li>
          <li>Returns a unique <code>userInterfacePaymentId</code></li>
          <li>Initial payment status is <a href="ob_paymentstatuses.html"><strong>PENDING</strong></a></li>
          <li>The URI must be passed to the PSU</li>
          <li>Bank Selection screen launches in a new browser window/tab when the user clicks the link</li>
        </ul>          
      </td>
    </tr>
    <tr>
      <td>-</td>
      <td>-</td>
      <td>
        The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> is redirected to authenticate and approve the payment on that <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP's</a> online banking portal.
		 Once the user approves or declines the payment he/she is redirected to the <code>merchantPostAuthUrl</code> (as referenced in the Create Payment call).
      </td>
    </tr>
	<tr>
      <td><a href="tok_reqtokorg.html"><span class="label label-info">POST</span></a></td>
      <td><a href="tok_reqtokorg.html">Access Token</a></td>
      <td>
        Pass your merchant API Key with the required scope = <code>openbanking_callback</code> to retrieve an OAuth access token.
      </td>
    </tr>
	<tr>
      <td><a href="ob_paymentcallback.html#forward-payment-callback-endpoint"><span class="label label-info">POST</span></a></td>
      <td><a href="ob_paymentcallback.html#forward-payment-callback-endpoint">Forward Payment Callback</a></td>
      <td>
        In this mode as the callback/redirect from the ASPSP does not go directly to the Nuapay TPP, it is required to forward the details via this service;
		you must pass your <code>callbackAccessToken</code> and the <code>callbackParams</code>
      </td>
    </tr>
    <tr>
      <td><a href="ob_retrievepayment.html#retrieve-payment-endpoint"><span class="label label-success">GET</span></a></td>
      <td><a href="ob_retrievepayment.html#retrieve-payment-endpoint">Retrieve Payment Status</a></td>
      <td>
        Retrieve the status of the payment.
      </td>
    </tr>
  </tbody>
</table>


For more details, see [Self-Hosted-Callback Payment Page Setup](ob_selfcallbackmerch.html).

## Checkout Mode

{% include tip.html content="The CHECKOUT integration can be problematic in the mobile flow on some devices. If you want to use the Nuapay UI, we recommend that you use the REDIRECT integration to avoid any issues."%}

{% include note.html content="<span style='color: #B0B0B0;'>CHECKOUT and REDIRECT are only available for merchants who want to process GBP payments; if you want to process EUR transactions then use the SELF-HOSTED integration.</span>" %}

<span style="color: #B0B0B0;">
As a partner, you will need to interact with the Nuapay Open Banking services on behalf of your merchants. In this example we will assume that you want to set up a payment for Merchant X but do not have the merchant identifier and need to query the `GET /organisations` service to retrieve it as a first step.

<span style="color: #B0B0B0;">Call the following services in this order:</span>

| [<span class="label label-success">GET</span>](tok_listorgs.html) | [Organisations](tok_listorgs.html) | <span style="color: #B0B0B0;">(Optional) For _Partners_ Use this service to retrieve the list of organisations/merchants under your entity. Use your Partner-level API Key and store the required merchant identifier.  |
| [<span class="label label-info">POST</span>](tok_reqtokorg.html) | [Access Token](tok_reqtokorg.html) | <span style="color: #B0B0B0;">Use this service to retrieve an OAuth token for the required merchant. Pass your API Key and merchantId with scope = `openbanking_pisp`. </span>|
| [<span class="label label-info">POST</span>](ob_createpayment.html#create-payment-endpoint) | [Create Payment](ob_createpayment.html#create-payment-endpoint) | <span style="color: #B0B0B0;">Call this service with the merchant access token; the Create Payment service generates an Open Banking payment object, returning a unique `userInterfacePaymentId` with an (initial) [status](ob_paymentstatuses.html) of `PENDING`. Apply the Nuapay-provided JS and CSS on your page to render the Bank Selection screen for your merchant's payers.</span> |
| - | - | <span style="color: #B0B0B0;">The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank (also referred to as the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a>) and is redirected to authenticate and approve the payment on that ASPSP's online banking portal. </span> |
| [<span class="label label-success">GET</span>](ob_retrievepayment.html#retrieve-payment-endpoint) | [Retrieve Payment Status](ob_retrievepayment.html#retrieve-payment-endpoint) | <span style="color: #B0B0B0;"> Retrieve the status of the payment. </span> |

<span style="color: #B0B0B0;">For more details on this see the [Checkout Setup](ob_checkoutoverview.html). </span>
