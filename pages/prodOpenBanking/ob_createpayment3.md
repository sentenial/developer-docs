---
title: Create Payment TESTING
keywords: Create Open Banking Payment
summary: "Create Open Banking Payment RESTful API"
sidebar: ob_sidebar
permalink: ob_createpayment3.html
folder: prodOpenBanking
toc: false
---

## API Details 

The Create Payment service generates an Open Banking payment object, returning a unique ``paymentId`` with an (initial) status of  ``PENDING_APPROVAL``.

{% include tip.html content="We recommend that you use a unique idempotency key with each unique Create Open Banking Payment request. The **x-idempotency-key** is a Header parameter in this API." %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
  <div>
<div role="tabpanel" class="tab-pane active" id="profile">


  <script type="text/javascript">
 
//location selector is the location to place the spinner into
//redocSite is the url of the redoc site to load

function loadRedoc(locationSelector, redocSite) {
jQuery('<div/>', {
    id: 'docs-jekyll',
    class: 'some-class',
    title: 'now this div has a title!'
}).appendTo('body');
$("#docs-jekyll").hide();
$("#docs-jekyll" ).load( redocSite );
var image = $('<img></img>');
image.attr('src', 'images/redoc_spinner.gif');
$(locationSelector).html(image);
}

//contentId the content to grab from redoc
//locationSelector where to paste the content
//timeref the timer we set going looking for the content (allows the cancel of the timer)
function getDocs(contentId,locationSelector, timerRef) {
                var div = document.getElementById(contentId);
                if(div) {
                                $(locationSelector).html(div);
                                clearInterval(timerRef);                                
                }
}


loadRedoc('#profileTabs', 'https://sentenial.github.io/open-banking-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/createPaymentUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>


</div>



</div>


{% include links.html %}
