---
title: E-Mandate Overlay JavaScript
keywords: E-Mandate Overlay JavaScript
summary: "Once you have retrieved an E-Mandate Token, add JavaScript to your calling Payment Page"
sidebar: em_sidebar
permalink: em_overlayjavascript.html
folder: prodEmandates
---

## Add JavaScript to your Site

Once you have retrieved the E-Mandate token you will need to add the following JavaScript to your calling page,

* ``EMandates.setToken``: The E-Mandate token uniquely identifies details about the merchant and payer, setting the token allows the session to reference this information.
* ``EMandates.setUrl``: Sets the URL from which the overlay is rendered, for production this should be, https://api.nuapay.com/emandate. For UAT this should be, https://sandbox.nuapay.com/emandate.
* ``EMandates.overlay``: Renders the e-mandate overlay.

The sample JavaScript below shows how you can render an e-mandate overlay, here we assume that your token is: 

``3d895152-724c-4547-a8ae-acefa2b73423:``



```html
<html>

	<head>;

		<meta name="viewport" content="width=device-width, initial-scale=1">

		<link href="https://api.nuapay.com/emandate/static/css/emandates-overlay.css" rel="stylesheet">

		<script src="https://api.nuapay.com/emandate/static/js/emandates-overlay.js">

		</script>

		<script>

			EMandates.setToken('3d895152-724c-4547-a8ae-acefa2b73423');

			EMandates.setUrl("http://api.nuapay.com/emandate");

		</script>

	</head>

	<body>

		<button onclick="EMandates.overlay();">€9.99 Sign Up Now!</button>

	</body>

</html>
````

You then need to call the overlay method for the ``onclick`` event on your calling Web page:

<p>
{% include image.html file="sign_overlay.png" alt="overlay button" %}
</p>


{% include links.html %}
