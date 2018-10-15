---
title: Adding a Response Handler
keywords: Adding a Response Handler
summary: "Add JavaScript to handle the reponse."
sidebar: em_sidebar
permalink: em_directapiresphandler.html
folder: prodEmandates
---

The Response handler allows you to process the response received from Nuapay and post details back to your server if required.

The following JavaScript illustrates how you might handle this:

````js
function successResponseHandler(statusCode, responseBody) {
		submitFormActionsDone();

		if (responseBody.data.mandateInfo.signed) {
			//deal with submitting form to the server
			//post to server the detail back
			var form = document.getElementById('milkManForm');
			
			//mandateid
			var mandateId = document.createElement("input");
			mandateId.setAttribute("type", "hidden");
			mandateId.setAttribute("name", "mandateId");
			mandateId.setAttribute("value", responseBody.data.mandateInfo.mandateId);
			form.appendChild(mandateId);
			//encodedMandateId
			var encodedMandateId = document.createElement("input");
			encodedMandateId.setAttribute("type", "hidden");
			encodedMandateId.setAttribute("name", "encodedMandateId");
			encodedMandateId.setAttribute("value", responseBody.data.mandateInfo.encodedMandateId);
			form.appendChild(encodedMandateId);
			//encodedSchemeId
			var encodedSchemeId = document.createElement("input");
			encodedSchemeId.setAttribute("type", "hidden");
			encodedSchemeId.setAttribute("name", "encodedSchemeId");
			encodedSchemeId.setAttribute("value", responseBody.data.mandateInfo.encodedSchemeId);
			form.appendChild(encodedSchemeId);
			
			form.submit();
			
		} else {
			dealWithUnexpectedError(responseBody);
		}
	}
````


{% include links.html %}
