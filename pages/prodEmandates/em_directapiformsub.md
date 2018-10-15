---
title: Processing the Form Submission
keywords: Processing the Form Submission
summary: "Add JavaScript to handle the form submission."
sidebar: em_sidebar
permalink: em_directapiformsub.html
folder: prodEmandates
---

You must register a JavaScript function that will be called prior to form submission, this function will post the mandate details, securely back to Nuapay.

The ``successResponseHandler/errorResponseHandler`` will later process the response from Nuapay and update your UI with either success or error details.

If your application processes a successful response you can append the details returned to your form and post them back to your server. This means you never have to process or store sensitive information like IBANs.

The key call here is ``Emandates.signEmandate``

````js
function submitForm() {

		var name = document.getElementById('name');
		var email = document.getElementById('email');
		var iban = document.getElementById('iban');

		var requestData = {
			"debtorDetails" : {
				"name" : name.value,
				"email" : email.value,
				"iban" : iban.value
			},
			"accepted" : true
		};
		Emandates.signEmandate(requestData, successResponseHandler,
				errorResponseHandler);
		return false;
	}
````


{% include links.html %}
