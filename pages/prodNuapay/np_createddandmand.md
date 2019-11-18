---
title: Create Direct Debit & Mandate
keywords: Create Direct Debit & Mandate
summary: "Create Direct Debit & Mandate RESTful API - generate a mandate and a payment in a single API call."
sidebar: np_sidebar
permalink: np_createddandmand.html
folder: prodNuapay
toc: false
---

## API Details

As outlined in the <a href= "np_createdirectdebit.html"> Create Direct Debit</a> call, you must have an active mandate before you can begin to collect Direct Debit payments. Typically you would use the <a href="np_createmandate.html">Create Mandate</a> call and then reference the successfully activated mandate when you create the Direct Debit payment.

The <b>Create Direct Debit and Mandate</b> call allows you to combine these separate requests into a single call; the request performs two operations:

* A mandate is created in Active status
* A Direct Debit payment is created and linked to the new mandate


{% include note.html content="A successful request will result in a new mandate and direct debit being created. If the request is unsuccessful neither a mandate nor a direct debit will be created." %}


The Create Direct Debit and Mandate request must include:

* A requested collection date for the Direct Debit payment
* The payment amount
* The payer's name
* The payer's IBAN
* The Merchant Nuapay IBAN

{% include swagger_np.html %}

{% include urls.html %}


<ul id="profileTabs" class="nav nav-tabs">
    
   
</ul>
   
{% include redoc.html %}
   
loadRedoc('#profileTabs', 'https://sentenial.github.io/nuapay-swagger/docs/redoc.html');
var timerRef = setInterval(function() { getDocs('operation/addSinglePaymentMOTFUsingPOST','#profileTabs',timerRef); }, 500);


</script>


<div id="mydiv"></div>
</div>
</div>


{% include links.html %}
