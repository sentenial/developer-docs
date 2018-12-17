---
title: WordPress Page Setup
keywords: WordPress Page Setup
summary: "Nearly there! Configuring your page through the WordPress dashboard is the final step."
sidebar: em_sidebar
permalink: em_wppagesetup.html
folder: prodEmandates
---

To set up your page with a new SIGN button:


<ol>
	<li value="1">Log on to your WordPress dashboard.</li>
	<li value="2">Select <b>Pages</b> from the left-hand menu:</li>
	<p>
		<img src="images/wp_pgsetup1.png" style="width: 279;height: 254;" />
	</p>
	<li value="3">Choose <b>Edit</b> to modify the page on which you want your payers to sign up for electronic mandates.</li>
	<li value="4">Add the following lines to your page (replacing the example API code, scheme ID and IBAN below with your own):</li>
	<table style="width: 100%;" class="Code">
		<col />
		<tbody>
			<tr>
				<td>[nuapay api_key="1TC1473798882f0b02c0a81017b3497cbb08d7813e1efffa7d495ffbeb0fctc0" scheme_type="CORE" payment_type="RCUR" scheme_id="IE26ZZZ123456123" creditor_iban="IE73AIBK12345446707123" integration_type="REDIRECT"]</td>
			</tr>
		</tbody>
	</table>
	<p>The code above includes the following details:</p>
	<ul>
		<li value="1">Your API key</li>
		<li value="2">Scheme Type </li>
		<li value="3">Payment Type</li>
		<li value="4">Scheme ID</li>
		<li value="5">Merchant IBAN</li>
		<li value="6">Integration Type (either REDIRECT&#160;or OVERLAY) - REDIRECT&#160;opens the mandate sign-up screen in a new tab or window; OVERLAY&#160;renders the mandate signing screen on top of the calling page so your customers have a seamless experience.</li>
	</ul>
	<li value="5">Save your changes and reload your page. Assuming you have not made any errors in the lines above you should see a new button being rendered on your page. The example below shows how an integration to the imaginary Nuapay Gym might look (the page's source and the resultant Web page):</li>
	<p>
		<img src="images/wp_gym1.png" style="width: 915;height: 700;" />
	</p>
</ol>





{% include links.html %}
