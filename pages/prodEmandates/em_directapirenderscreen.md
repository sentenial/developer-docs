---
title: Rendering the E-Mandate Screen
keywords: E-Mandate Rendering
summary: "Add JavaScript to render the screen based on the E-mandate token returned."
sidebar: em_sidebar
permalink: em_directapirenderscreen.html
folder: prodEmandates
---

The E-Mandate token that is returned following your <a href ="em_tokendirectapi.html">Prepare E-Mandate</a> request is used to render the E-Mandate screen.

In your Web page you must include the following JavaScript file reference:

````js
<script src="/emandate/static/js/emandates.js">
````

In addition, two elements must be added to your Web page:

1. The API Endpoint
1. The E-Mandate Token

````js
<script> 

/*<![CDATA[*/ 



EMandates.setToken('07e43737-22d5-491e-9dd1-423e2270d190'); 


EMandates.setUrl('https://api.nuapay.com/emandate-rest'); 

</script>
````

This piece of script allows your application to submit your customer's mandate details to Nuapay prior to submitting the data to your own server.

{% include links.html %}
