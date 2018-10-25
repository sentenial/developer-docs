---
title: Payment Page Setup
keywords: Payment Page Setup Javascript Add Open Banking Payment Page
summary: "Adding Open Banking as a payment option to your Payment Page requires a little configuration as outlined below."
sidebar: ob_sidebar
permalink: ob_setupoverview.html
folder: prodOpenBanking
---

## Overview

To add Open Banking to your payment page you will need to carry out the following steps:

1. Retrieve your API Key - contact our Client Support team if you do not have a key.
1. Generate a unique Payment ID.
1. Include a reference to a CSS and JS file on your payment page.
1. Add a button to your page.
1. Add a JavaScript Event Listener to detect when the payment UI pop-up window closes.

## Retrieving Your API Key

An API Key uniquely identifies you on Nuapay and is required to allow you to use our API services.

For more on API Keys, see the <a href="ob_generalrules.html">API Basics</a> section.


## Generating a Unique Payment ID

Each Open Banking payment requires a unique payment identifier. 

To generate a payment ID:

1. Generate a server-to-server call to ``/payments``.
1. Ensure that you have referenced your API Key in the request.
1. The ``/payments`` service is described in <a href="ob_createpayment.html">Create Payment</a>.

{% include tip.html content="To see an Open Banking payment page in action, see our Showcase sample: [Open BankingShowcase](https://merchant.nuapay.com/merchant/shop). If you select the Ozone Bank, use mits and mits as user name and password. If you select Nuapay as your bank then user name and password is psu and psu." %}

## Adding the CSS and JS File References

On your payment page you will need to add the following:

**For Sandbox**

````
<script src="https://tpp-sandbox.nuapay.com/tpp-ui/js/nuapay-open-banking.js"></script>
<link rel="stylesheet" type="text/css" href="https://tpp-sandbox.nuapay.com/tpp-ui/css/nuapay-open-banking.css" />
````

**For Production**

````
<script src="https://tpp.nuapay.com/tpp-ui/js/nuapay-open-banking.js"></script>
<link rel="stylesheet" type="text/css" href="https://tpp.nuapay.com/tpp-ui/css/nuapay-open-banking.css" />
````

## Adding The Open Banking Pay Button

At this point you have:

* Added the JS and CSS links to your payment page.
* Retrieved the payment ID (via the Create Payment service).

To enable the **Pay** button you will need to add an ``onclick`` event. See the example below:

````
<a class="btn btn-primary" href="#" onclick="NuapayOpenBanking.showUI(‘gabxrlvbl5’;’https://tpp-sandbox.nuapay.com/tpp-ui/’);">Pay Now</a>

````

This button will open the Select Banks pop-up for the Payment ID ``gabxrlvbl5``

``https://tpp.nuapay.com/tpp-ui/`` is the location of the Nuapay TPP User Interface, which will allow your customers to select their bank.
Note that there is a Sandbox and Production TPP for this so you will need to specify the correct URL based on whether you are testing or working in Production:

|SANDBOX|https://tpp-sandbox.nuapay.com/tpp-ui/|
|PRODUCTION| https://tpp.nuapay.com/tpp-ui/|

## Adding a Listener

Once you have successfully added the **Pay** button to your site you will next need to handle when the pop-up window is closed.
In a successful flow the pop-up will be closed by users after they confirm the payment with their bank and are redirected to your confirmation message. Users may also choose to cancel out of the flow at any point and close the pop-up window without completing the payment.

To manage the closing of the pop-up window, you will need to add a Listener to your parent Payment Page window to <i>listen</i> for the close event, which (for Payment ID  gabxrlvbl5) would look like this:

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

Here we are checking that the event is a closed event, in this example the merchant is calling back to their own server. 

The call is to ``/merchant/status?id=gabxrlvbl5``


{% include note.html content="On closing of the pop-up window you must make a server-to-server call to retrieve the payment status (using the [Retrieve Payment](ob_retrievepayment.html) service)." %}

{% include links.html %}






