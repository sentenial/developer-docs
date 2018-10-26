---
title: E-Mandate Redirect for Mandate Signing
keywords: E-Mandate Redirect for Mandate Signing
summary: "Handling Mandate Signing via JavaScript on your payment page."
sidebar: em_sidebar
permalink: em_redirectmdtsigning.html
folder: prodEmandates
---

After you have retrieved your E-Mandate token, you need to add some JavaScript to your Web site page to handle the redirect.

Your JavaScript needs to include:

* The appropriate references to the E-Mandate REST endpoints
* A reference to the E-Mandate token
* A Redirect function

If we assume that the E-Mandate token returned in the <a href= "em_tokenredirect.html">Prepare E-Mandate Token</a> request was:

``07e43737-22d5-491e-9dd1-423e2270d190``

Then your Web site script would need to be similar to the following

```js
<script> /*<![CDATA[*/

EMandates.setToken('07e43737-22d5-491e-9dd1-423e2270d190');

EMandates.setUrl('https://api.nuapay.com/emandate-rest');

EMandatesUI.setUrl('https://api.nuapay.com/emandate');

function redirect() { window.location = 'https://api.nuapay.com/emandate/emandate/web/show?token=07e43737-22d5-491e-9dd1-423e2270d190'; }; /*]]>*/

</script>
````

The redirect() method is then called to redirect your payer to the E-Mandate platform with the ``onclick`` event:

<img src="images/sign_overlay.png">

{% include links.html %}
