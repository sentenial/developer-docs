---
title: Use Cases
keywords: Use Cases
summary: "The following Use Cases should give you some good ideas of how best to implement a solution for your particular business. It gives a typical use case and the API requests and Webhooks that we'd recommend to implement."
sidebar: resources_sidebar
permalink: np_usecases.html
folder: prodNuapay
toc: false
---


## Overview

The following is a list of some of the most common Nuapay use cases:

<div class="panel-group" id="accordion">

<!-- START PANEL -- REM to update href=#collapse<n> for each new panel-->
<div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse1">Handling Paper Mandates...</a>
                            </h4>
                        </div>
                        <div id="collapse1" class="panel-collapse collapse noCrossRef">
                            <div class="panel-body">

                             <table>
    <tbody>
		<tr>
			<td>Use Case </td>
			<td>Mandate / Direct Debit Setup</td>
			<td>Description</td>
			<td>API Requests</td>
		</tr>
		<tr>
			<td width = "25%">
				<p>
					<b>Business</b>: A gym where members pay once per month. The fee is typically €50 per month.</p>
				<p>
					<b>Scenario</b>: A paper mandate is received and you want to activate it and add a series of Direct Debit payments.</p>
			</td>
			<td width = "20%">
				<p>
					<b>Mandate Setup</b>: Paper mandates are used</p>
				<p>
					<b>Direct Debit Setup</b>: Each member is configured with a schedule for 12 payments, which are collected monthly, on the 15th or the next business day.</p>
			</td>
			<td width ="25%">
				<ol>
					<li value="1">When a paper mandate is received, the details are reviewed to ensure they are correct.</li>
					<li value="2">Use <a href="np_createmandate.html">Create Mandate</a> to set up your mandate; it is created in Active status. </li>
					<li value="3">Use <a href="np_createschedule.html">Create Payment Schedule</a> to link a schedule to the mandate in step 2; payments are collected on the 15th of each month.</li>
					<li value="4">FInally use <a href="np_listdirectdebits.html">List Direct Debits</a> to view the list of Direct Debit payments linked to the schedule created in step 3.</li>
				</ol>
			</td>
			<td width = "100%">
				<ul>
					<li value="1">
						<a href="np_createmandate.html">Create Mandate</a>
					</li>
					<li value="2">
						<a href="np_createschedule.html">Create Payment Schedule</a>
					</li>
					<li value="3">
						<a href="np_listdirectdebits.html">List Direct Debits</a>
					</li>
				</ul>
			</td>
		</tr>
	</tbody>
</table>

                            </div>
                        </div>
                    </div>
                    <!-- END PANEL -->

                    <!-- START PANEL-->
<div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse2">Working with Wordpress and E-Mandates...</a>
                            </h4>
                        </div>
                        <div id="collapse2" class="panel-collapse collapse noCrossRef">
                            <div class="panel-body">

                                <table style="width: 100%;" class="Code">
	<col style="width: 191px;" />
	<col style="width: 258px;" />
	<col style="width: 314px;" />
	<col />
	<tbody>
		<tr>
			<td >Use Case </td>
			<td >Mandate / Direct Debit Setup</td>
			<td >Description</td>
			<td >API Requests</td>
		</tr>
		<tr>
			<td width ="20%">
				<p>
					<b>Business</b>: A charity seeking small donations of €5 </p>
				<p>
					<b>Scenario</b>: Once-off , small-value payments are collected. E-mandates are used to generate mandates</p>
				<p>&#160;</p>
			</td>
			<td width ="25%">
				<p>
					<b>Mandate Setup</b>: E-Mandates, using the WordPress Plug-in approach</p>
				<p>
					<b>Direct Debit Setup</b>:&#160;Once-off payments added via the Nuapay User Interface</p>
			</td>
			<td width ="25%">
				<ol>
					<li value="1">Payers choose to make a donation and opt to pay with a once-off direct debit. They log on to your WordPress Mandate signing page. See <a href="em_wpoverview.html">WordPress plug-in</a>. </li>
					<li value="2">Mandates are created as once-off (payment_type="OOFF" - see <a href="em_wppagesetup.html">WordPress Page Setup</a>). These mandates are created in Active status.</li>
					<li value="3">Email notifications inform you when new mandates are signed.</li>
					<li value="4">Log on to the Nuapay User Interface to add the €5 payment to the required mandates.</li>
				</ol>
			</td>
			<td width ="100%">
				<p>N/A </p>
				<p>(<i>all API&#160;requests are handled through the WordPress plugin and via the Nuapay User Interface</i>)</p>
			</td>
		</tr>
	</tbody>
</table>





                            </div>
                        </div>
                    </div>
                <!-- END PANEL -->

                <!-- START PANEL-->
<div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse3">Cancelling a Subscription... </a>
                            </h4>
                        </div>
                        <div id="collapse3" class="panel-collapse collapse noCrossRef">
                            <div class="panel-body">

                                <table style="width: 100%;" class="Code">
	<col style="width: 191px;" />
	<col style="width: 258px;" />
	<col style="width: 314px;" />
	<col />
	<tbody>
		<tr>
			<td>Use Case </td>
			<td>Mandate / Direct Debit Setup</td>
			<td>Description</td>
			<td>API Requests</td>
		</tr>
		<tr>
			<td width = "20%">
				<p>
					<b>Business</b>: A large magazine subscription service. </p>
				<p>
					<b>Scenario</b>: A user has requested that her subscription is cancelled. She has provided her mandate reference.</p>
			</td>
			<td width = "25%">
				<p>
					<b>Mandate Setup</b>: E-Mandates are used</p>
				<p>
					<b>Direct Debit Setup</b>: The customer currently has a payment schedule configured. She has paid 6 of her 12 payments.</p>
			</td>
			<td width = "25%">
				<ol>
					<li value="1">Call <a href="np_retrievemandate.html">Retrieve Mandate</a>, passing in the Unique Mandate Reference.</li>
					<li value="2">Use the returned resource mandate ID as an argument in the <a href="np_cancelmandate.html">Cancel Mandate</a> request.</li>
					<li value="3">Confirm that the mandate's status is CANCELLED in the response.</li>
					<li value="4">Optionally call <a href="np_listdirectdebits.html">List Direct Debits</a> (passing the Mandate ID returned in step 1) to confirm that all remaining payments in the schedule have been cancelled.</li>
				</ol>
			</td>
			<td width = "100%">
				<ul>
					<li value="1">
						<a href="np_retrievemandate.html">Retrieve Mandate</a>
					</li>
					<li value="2">
						<a href="np_cancelmandate.html">Cancel Mandate</a>
					</li>
					<li value="3">
						<a href="np_listdirectdebits.html">List Direct Debits</a>
					</li>
				</ul>
			</td>
		</tr>
	</tbody>
</table>






                            </div>
                        </div>
                    </div>
                <!-- END PANEL -->

                <!-- START PANEL-->
<div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse4">Reconcile payments related to a specific settlement date...</a>
                            </h4>
                        </div>
                        <div id="collapse4" class="panel-collapse collapse noCrossRef">
                            <div class="panel-body">

                                <table style="width: 100%;" class="Code">
	<col style="width: 191px;" />
	<col style="width: 258px;" />
	<col style="width: 314px;" />
	<col />
	<tbody>
		<tr>
			<td>Use Case </td>
			<td>Mandate / Direct Debit Setup</td>
			<td>Description</td>
			<td>API Requests</td>
		</tr>
		<tr>
			<td width = "20%">
				<p>
					<b>Business</b>: A large utility, supplying cable television and Internet services</p>
				<p>
					<b>Scenario</b>: A large monthly collection has been made; the Finance team want to reconcile all payments on a daily basis.</p>
			</td>
			<td width = "25%">
				<b>Mandate Setup</b>: E-Mandates are used<p>
					<b>Direct Debit Setup</b>: Customers are all configured on open-ended schedules with collections being taken on the 10th of each month.</p>
			</td>
			<td width = "25%">
				<ol>
					<li value="1">Payments are automatically generated as per the configured schedules with a collection date on the 10th .</li>
					<li value="2">Payments are exported two days prior to the settlement date. Pre-settlement Rejects begin to be received from some payers' banks on the 8th and 9th of the month.</li>
                    <li value="3">Use <a href="np_listfaileddds.html">List Failed Direct Debits</a> to retrieve details of the transactions that have been rejected prior to the settlement date. Use a date range in your request to return the relevant transaction details. Note: We highly recommend that you use the List Failed Direct Debits request every day, specifying the previous business day as the 'From' and 'To' parameters; doing this will ensure that you have a good indication of your Direct Debit payments' statuses every day.							
						 </li>
					<li value="4">Use <a href="np_listdirectdebits.html">List Direct Debits</a> and pass in the 10th as the 'collection date to' and 'collection date from'. This will give you the status of all payments.</li>
					<li value="5">Re-run <a href="np_listfaileddds.html">List Failed Direct Debits </a>daily (or possibly more often, if required) after the settlement date  to retrieve any additional post-settlement Returns or Refunds.</li>
					<li value="6">The details of the response should be captured to export to a report so that your Finance team can fully reconcile all your payers' accounts.</li>
				</ol>
			</td>
			<td width = "100%">
				<ul>
					<li value="1">
						<a href="np_listfaileddds.html">List Failed Direct Debits</a>
					</li>
					<li value="2">
						<a href="np_listdirectdebits.html">List Direct Debits</a>
					</li>
				</ul>
			</td>
		</tr>
	</tbody>
</table>







                            </div>
                        </div>
                    </div>
                <!-- END PANEL -->


                 <!-- Final -->

                    </div>





{% include links.html %}
