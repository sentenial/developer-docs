---
title: Create Payment Schedule & Mandate
keywords: Create Payment Schedule & Mandate
summary: "Create Payment Schedule & Mandate RESTful API"
sidebar: np_sidebar
permalink: np_createschedulemandate.html
folder: prodNuapay
toc: false
---

## API Details

As outlined in <a href = "np_createschedule.html">Create Payment Schedule</a>, before you can add a schedule of Direct Debit payments for a payer you must first have an Active mandate in place; so two separate requests are required: one to create and activate a mandate and a second to add the schedule of payments.

The <b>Create Payment Schedule and Mandate</b> request allows you to combine these two request so that you can create a mandate and a payment schedule in a single request.

{% include note.html content="A successful request will result in a new mandate and a schedule of direct debits being created. If the request is unsuccessful neither a mandate nor any direct debits will be created." %}


<ul id="profileTabs" class="nav nav-tabs">
    <li class="active"><a href="#profile" data-toggle="tab">Request</a></li>
    <li><a href="#about" data-toggle="tab">Response</a></li>
   
</ul>
  <div class="tab-content">
<div role="tabpanel" class="tab-pane active" id="profile">


  <table>
<colgroup>
<col width="30%" />
<col width="90%" />
</colgroup>

<tbody>
<tr>
<td markdown="span">Usage</td>
<td markdown="span">Both the schedule and mandate details must be provided</td>
</tr>
<tr>
<td markdown="span">Method</td>
<td markdown="span"><span class="label label-info">POST </span>
</td>
</tr>
<tr>
<td markdown="span">URI</td>
<td markdown="span">/schemes/{CS_ID}/paymentschedules
</td>
</tr>
<tr>
<td markdown="span">Required Arguments</td>
<td markdown="span"><b>paymentFrequency</b>
<br/><i>Possible values: DAILY, WEEKLY, BIWEEKLY, MONTHLY, YEARLY, CUSTOM</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>paymentType</b>
<br/><i>FIXED_LENGTH, OPEN_ENDED</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>startDate</b>
<br/><i>The Settlement Date of the first payment in the schedule</i>
</td>
</tr>
<tr>
<td markdown="span"></td>
<td markdown="span"><b>paymentAmount</b>
<br/><i>The value of the regular payment to be collected. Max length without decimals is 12 digits. Decimal separator is "." A maximum of two decimal places is allowed. 
<br/><br/>  Note: Other arguments may be required depending on your schedule requirements (for example if you are setting up a FIXED_LENGTH schedule then the <b>numberOfPayments</b> is mandatory).
</i>
</td>
</tr>
</tbody>
</table>



</div>

<div role="tabpanel" class="tab-pane" id="about">
<p>A successful request will return a <b>201 Created</b> response code</p>
<p>The following is the complete list of possible status codes, which may be returned in the response:</p>
    {% include httpcodes.html %}
    
 
    </div>


</div>

<b>Note:</b> For a more detailed view of this API see the: <a href="https://docs.nuapay.com/v1/#create-schedule-mandate" target = '_blank'><i class="fa fa-cogs"></i> API Reference</a>


<!--{% include swaggerlink.html %}-->

{% include links.html %}
