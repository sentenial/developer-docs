---
title: Create Account Access
keywords: Create Account Access Open Banking 
summary: "Create Account Access RESTful API"
sidebar: ob_sidebar
permalink: ob_createaccountaccess.html
folder: prodOpenBanking
toc: false
---

## API Details

The Create Account Access service generates the account request that the end user must agree to in order for you, as merchant, to access specific account details.

{% include tip.html content="You must know the bank in which your customer's account is held; this is passed as the <b>x-tpp-bank-id</b> value in your API Header parameter. Use the <b>GET /banks</b> service to retrieve the required Bank ID. " %}

<!--
{% include swagger_ob.html %}

<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
 

 {% include redoc.html %}

loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/createAccountRequestUsingPOST','#profileTabs',timerRef); }, 500);

</script>


<div id="mydiv"></div>


</div>



</div>
-->

{% include note.html content="Swagger samples are currently not published for our AISP services. Contact [api.support@nuapay.com](mailto:api.support@nuapay.com) if you need more information on AISP" %}


{% include links.html %}