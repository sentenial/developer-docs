---
title: E-Mandate Overlay JavaScript
keywords: E-Mandate Overlay JavaScript
summary: "Once you have retrieved an E-Mandate Token, add JavaScript to your calling Payment Page"
sidebar: em_sidebar
permalink: em_overlayjavascript.html
folder: prodEmandates
toc: false
---

## Add JavaScript to your Site

* After you have retrieved your [E-Mandate token](em_token.html), you need to add some JavaScript to your page.
* You must reference the Nuapay `.js` and a `.css` file.
* You will need to references either the Sandbox or the Production environment:

|**Environment**|**JS Link**|**CSS Link**|
|**Sandbox**|https://sandbox.nuapay.com/emandate/static/js/emandates-integration.js | https://sandbox.nuapay.com/emandate/static/css/emandates-overlay.css |
|**Production**|https://api.nuapay.com/emandate/static/js/emandates-integration.js | https://api.nuapay.com/emandate/static/css/emandates-overlay.css |

To set up your page (for Sandbox):
1. Use the following JS and CSS references:
  ```js
  <script type='text/javascript' src="https://sandbox.nuapay.com/emandate/static/js/emandates-integration.js"></script>
	<link rel="stylesheet" type="text/css" href="https://sandbox.nuapay.com/emandate/static/css/emandates-overlay.css"/>
  ````
1. Add the following script (replacing `90c72f56-5c12-4bd0-aad8-371c5a1db617-24j8rvwov2`, in this example, with the retrieved [E-Mandate token](em_token.html)):
  ```js
  <script>
    /*<![CDATA[*/
     EMandates.setToken("90c72f56-5c12-4bd0-aad8-371c5a1db617-24j8rvwov2");
     EMandates.setUrl("https://sandbox.nuapay.com/emandate");    
     };
     /*]]>*/
  </script>
  ````
1. Finally call the overlay method for the ``onclick`` event on your calling Web page:
   <img src="images/sign_overlay.png">


{% include links.html %}
