---
title: WordPress Plugin Configuration
keywords: WordPress Configuration
summary: "Once you have installed the plugin there are some final configuration steps required to complete the integration."
sidebar: em_sidebar
permalink: em_wpconfig.html
folder: prodEmandates
---

Once you have successfully <a href="em_wpinstall.html">installed the plugin</a>, some additional configuration is required:


<ol>
	<li value="1">Open your WordPress dashboard.</li>
	<li value="2">Select <b>Settings &gt; NUAPAY&#160;Options</b>.</li>
	<p>
		<img src="images/wp_config1.png" style="width: 408;height: 449;" />
	</p>
	<li value="3">Add the following URLs:<ol>
			<li value="1">
				<b>API&#160;KEY&#160;URL</b>: https://api.nuapay.com/v1/emandates</li>
			<li value="2">
				<b>EMANDATE URL</b>: https://api.nuapay.com/emandate/web</li>
		</ol>
	</li>
	<p>
		<img src="images/wp_config2.png" style="width: 500;height: 331;" />
	</p>
	<li style="font-weight: normal;" value="4">Click <b>Save Changes</b>.</li>
</ol>


{% include important.html content="Note that some Web Hosting service providers use caching to improve the overall speed and performance for their sites. This means that rather than serve a HTML page every time it receives a HTTP request from a client, the Web Server may provide a page from its cache. Because the mandate signing screen contains confidential data and must be unique for every client,  caching should be disabled for the Nuapay plug-in. Please confirm with your Hosting provider that any page that has the Nuapay shortcode embedded is added to their no-cache whitelist." %}


The final step in your WordPress integration is to add the [Sign Up button](em_wppagesetup.html) to your required WordPress Web page.


{% include links.html %}
