---
title: Checkout Payment Page Setup
keywords: Checkout Payment Page Setup Javascript Add Open Banking Payment Page
summary: "Adding Open Banking (Checkout mode) as a payment option to your Payment Page requires a little configuration as outlined below. In Checkout mode you will use the Nuapay user interface for Bank Selection and Confirmation screens."
sidebar: ob_sidebar
permalink: ob_checkoutoverview.html
folder: prodOpenBanking
---

{% include note.html content="This section is for **Partner** users who want to use the **CHECKOUT** mode - see [Implementation Options](ob_pispimplementation.html) for more on this." %}

## Overview

In **Checkout** mode you will: 

1. Use your partner-level API key to retrieve a token representing the required merchant. (For more on this see [list organisations](ob_partnerintegration.html#api-details---get-organisations) and [retrieving tokens](ob_partnerintegration.html#api-details---post-tokens)).
1. Call the `/payments` endpoint, on behalf of the merchant, using the OAuth token retrieved in the previous step (see [Create Payment](ob_createpayment.html)) and set the `integrationType` to `CHECKOUT`. Manage the returned payment identifier with some Nuapay-provided JS and CSS to render the Bank Selection screen for your payers. 
1. The <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> selects a bank.
1. Redirect the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> to authorise the payment.
1. Process the callback URL; display the status to the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSU</a> and close the TPP UI, passing control to the parent window.
1. Use [Retrieve Payment](ob_retrievepayment.html) to determine the final payment status, if required (an optional step). 

A detailed overview of the various steps involved in this flow is provided in the image below.

{% include tip.html content="Click Extend from the top menu to enlarge or click the image itself to open it in a new browser tab/window" %}

{% include image.html file="ob_checkout_flow.png" url="images/ob_checkout_flow-partner.png" target = "_new" alt="Checkout Flow - Partner" caption="CHECKOUT Flow - Partner" %}

## Authorisation 

An API Key or OAuth token uniquely identifies you on Nuapay and is required to allow you to use our API services.

For more on API Keys and OAuth, see the <a href="ob_generalrules.html">API Basics</a> section.


## Generating a Unique Payment ID 

The Open Banking payment endpoint returns a payment identifier on a sucessful invocation. 

To generate a payment ID:

1. Generate a server-to-server call to `/payments`.
1. Ensure that you have referenced your API Key or OAuth token in the request.
1. The ``/payments`` service is described in <a href="ob_createpayment.html">Create Payment</a>.


## Adding the CSS and JS File References

On your payment page you will need to add the following:

**For Sandbox**

````
<script src="https://sandbox.nuapay.com/tpp-ui/js/nuapay-open-banking.js"></script>
<link rel="stylesheet" type="text/css" href="https://sandbox.nuapay.com/tpp-ui/css/nuapay-open-banking.css" />
````

**For Production**

````
<script src="https://api.nuapay.com/tpp-ui/js/nuapay-open-banking.js"></script>
<link rel="stylesheet" type="text/css" href="https://api.nuapay.com/tpp-ui/css/nuapay-open-banking.css" />
````

## Adding The Open Banking Pay Button

At this point you have:

* Added the JS and CSS links to your payment page.
* Retrieved the payment ID (via the Create Payment service).

To enable the <span class="label label-info">PAY</span> button you will need to add an ``onclick`` event. See the example below:

````
<a class="btn btn-primary" href="#" onclick="NuapayOpenBanking.showUI(‘gabxrlvbl5’;‘https://sandbox.nuapay.com/tpp-ui/’);">Pay Now</a>

````

This button will open the Select Banks pop-up for the Payment ID ``gabxrlvbl5``

``https://sandbox.nuapay.com/tpp-ui/`` is the location of the Nuapay TPP User Interface, which will allow your customers to select their bank.


{% include tip.html content="To avoid any issues with **pop-up blockers**, we recommend that you request your users to: <br/>
<br/>1. Click a button to pay by Open Banking (allowing you to retrieve the paymentId) 
<br/>2. Click a second button to choose a bank (launching the pop-up with the paymentId retrieved in step 1)
<br/><br/>Because launching the Select Bank screen in step 2 is a user-initiated action, your users will not be prompted to enable pop-ups.
" %}

Note that there is a Sandbox and Production TPP for this so you will need to specify the correct URL based on whether you are testing or working in Production:

|SANDBOX|https://sandbox.nuapay.com/tpp-ui/|
|PRODUCTION| https://api.nuapay.com/tpp-ui/|


## Adding a Listener

Once you have successfully added the <span class="label label-info">PAY</span> button to your site you will next need to handle when the pop-up window is closed.
In a successful flow: 

* The pop-up will be closed by users after they confirm the payment with their bank and are redirected to your confirmation message. 
* Users may also choose to cancel out of the flow at any point and close the pop-up window without completing the payment.

To manage the closing of the pop-up window, you will need to add a Listener to your parent Payment Page window to <i>listen</i> for the close event, which (for Payment ID  `gabxrlvbl5`) would look like this:

``{"status":"CLOSED","paymentId":" gabxrlvbl5"}``


A Sample Listener is provided below.


````
<script>

var listener = function(event) {
    if(event.data.status=="CLOSED") {
        var url = "/merchant/status?id=" + event.data.paymentId;
        $.ajax({
          url: url,
          success: function(data){
            if (data.status == "COMPLETE") {
                location.replace("./shoppaid");
            } else {
                location.replace("./shopfailed");
            }
          },
          error: function(){
            location.replace("./error");
          }
        });
    }
}

window.addEventListener("message",listener,false);

</script>
````

Here we are checking that the event is a closed event, in this example the merchant is calling back to their own server to get the payment status. 

The call is to ``/merchant/status?id=gabxrlvbl5``


{% include note.html content="On closing of the pop-up window you must make a server-to-server call to retrieve the payment status (using the [Retrieve Payment](ob_retrievepayment.html) service). See [Payment Statuses](ob_paymentstatuses.html) for more on the possible statuses." %}

## The End-User Experience

Once configured your users' interaction with Open Banking payments will be similar to the following:

The PSU (i.e. the end user) will select the required goods or services on your merchant site and:

1. Select **Nuapay Open Banking** as the payment method.
1. Click **Pay**.
1. A pop-up window overlayed on the calling payment page is generated. This is rendered through Nuapay's TPP application:<br/>
<img src = "images/ob_1_selectbnk3.png">
1. The user selects the <i>ASPSP</i> (i.e. the bank) in which his account is held (Barclays for example) and clicks **Continue**.
1. A confirmation of the bank selected is displayed and the user clicks **Confirm**.
1. The user is then redirected to his bank where he must sign on with his online banking credentials:
<img src="images/ob_2_bnklogon.png">
1. Once successfully signed on the user can choose to **Confirm** the payment to the merchant:
<img src ="images/ob_3_bnkconfirm.png">
1. The payment is authorised and the payer (PSU) is redirected to the Nuapay TPP with a confirmation message:
<img src="images/ob_4_conf.png">
1. The pop-up window may be closed by the payer (or may close automatically) and the user is redirected to the merchant payment page, with a confirmation message.

{% include callout.html content="On successful completion of this payment flow your customer has provided his/her consent for the payment to be collected for the selected account. The actual funds transfer to your account may happen within a matter of seconds or it may be processed on the following business day. The speed with which funds are transferred to your account is controlled by your customers' banks and is determined by the default payment scheme they are using. A scheme like SEPA CT Instant (for Euro payments) or Faster Payments (for GBP payments) will result in funds being credited to your account within seconds. Schemes like SEPA CT and BACS Credit will generally take a business day to process. Nuapay uses the [Payment Received Webhook](ob_whreceived.html) to notify you when funds are settled to your Nuapay account (Note: only available if you are using a Nuapay account)." type="primary" %}



{% include links.html %}






