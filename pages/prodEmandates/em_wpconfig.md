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


The final step in your WordPress integration is to add the Sign Up button to your required WordPress Web page.


{% include links.html %}
