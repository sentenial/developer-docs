---
title: Checkout Event Handler
keywords: E-Mandate Checkout Event Handler
summary: "Registering an Event Handler"
sidebar: em_sidebar
permalink: em_overlayeventhandler.html
folder: prodEmandates
---

Once you have added the ``onclick`` method to your button you next need to register an Event Handler.

This event handler can:

* Allow you to provide your payer with a meaningful message on screen
* Let you manage the returned encrypted mandate ID so that the value is stored on your server and available to be used later when creating payments, for example.

Your Event Handler script might be similar to the following sample:


```js
<script>
	function demoEventListener(event) {
		var data = event.data;
		if (data.type === "EMANDATES") {

			if (data.status == "CANCEL") {
				var button = document.getElementById('signup');
				button.className = "btn btn-warning btn-xl";
				button.innerHTML = 'Mandate Process Cancelled';
			} else if (data.status == "FAILURE") {
				var button = document.getElementById('signup');
				button.className = "btn btn-danger btn-xl";
				button.innerHTML = 'Mandate Not Created Due To Error';
				var overlay = document.getElementById('nuapayoverlay');
				overlay.style = "visibility: hidden;"

			} else if (data.status == "SUCCESS") {
				var button = document.getElementById('signup');
				button.className = "btn btn-success btn-xl";
				button.innerHTML = 'Mandate Created Welcome On Board!';
				var overlay = document.getElementById('nuapayoverlay');
				overlay.style = "visibility: hidden;"
			}
			document.getElementById('nuapayoverlay').setAttribute("style","visibility:hidden");
			document.getElementById('page-top').setAttribute("style","");
			}
	}
	window.addEventListener("message", demoEventListener, false);
</script>
````

{% include note.html content="See the Checkout approach in action on our [Showcase site](https://showcase.nuapay.com/showcase/movie-flix)" %}




{% include links.html %}
