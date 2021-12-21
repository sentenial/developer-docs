---
title: E-Mandate Redirect for Mandate Signing
keywords: E-Mandate Redirect for Mandate Signing
summary: "Handle the Mandate Signing via JavaScript on your payment page."
sidebar: em_sidebar
permalink: em_redirectmdtsigning.html
folder: prodEmandates
---

* After you have retrieved your [E-Mandate token](em_tokenredirect.html), you need to add some JavaScript to your Web site page to handle the redirect.
* To set up your page you will need to reference a Nuapay `.js` file and add some JavaScript.
* You must reference either the Sandbox or the Production JavaScript file:

|**Sandbox**|https://sandbox.nuapay.com/emandate/static/js/emandates-integration.js |
|**Production**|https://api.nuapay.com/emandate/static/js/emandates-integration.js |

To set up your page (for Sandbox):
1. Use the following JS reference:
  ```js
  <script type='text/javascript' src="https://sandbox.nuapay.com/emandate/static/js/emandates-integration.js"></script>
  ````
1. Add the following script (replacing `90c72f56-5c12-4bd0-aad8-371c5a1db617-24j8rvwov2`, in this example, with the retrieved [E-Mandate token](em_tokenredirect.html)):
  ```js
  <script>
    /*<![CDATA[*/
     EMandates.setToken("90c72f56-5c12-4bd0-aad8-371c5a1db617-24j8rvwov2");
     EMandates.setUrl("https://sandbox.nuapay.com/emandate");

     function redirect() {
     EMandates.redirect();
     };

     /*]]>*/
  </script>
  ````
1. Finally, call the redirect() method to send your payer to the E-Mandate platform with the ``onclick`` event:
   <img src="images/sign_redirect.png">

{% include links.html %}
