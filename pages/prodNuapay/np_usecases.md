---
title: Use Cases
keywords: Use Cases
summary: "The following Use Cases should give you some good ideas of how best to implement a solution for your particular business. It gives a typical use case and the API requests and Webhooks that we'd recommend to implement."
sidebar: np_sidebar
permalink: np_usecases.html
folder: prodNuapay
toc: false
---


## Working with Paper Mandates

Your business uses paper mandates and you want to create an active mandate and add a series of payments to it:

<div class="panel-group" id="accordion">

<div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseOne">Use Case Details >></a>
                            </h4>
                        </div>
                        <div id="collapseOne" class="panel-collapse collapse noCrossRef">
                            <div class="panel-body">
                                
                                <table style="width: 100%;" class="Code">
	<col style="width: 191px;" />
	<col style="width: 258px;" />
	<col style="width: 314px;" />
	<col />
	<tbody>
		<tr>
			<td style="color: #f5f5f5;background-color: #808080;">Use Case </td>
			<td style="color: #f5f5f5;background-color: #808080;">Mandate / Direct Debit Setup</td>
			<td style="color: #f5f5f5;background-color: #808080;">Description</td>
			<td style="color: #f5f5f5;background-color: #808080;">API Requests</td>
		</tr>
		<tr>
			<td>
				<p>
					<b>Business</b>: A gym where members pay once per month. The fee is typically €50 per month.</p>
				<p>
					<b>Scenario</b>: A paper mandate is received and you want to activate it and add a series of Direct Debit payments.</p>
			</td>
			<td>
				<p>
					<b>Mandate Setup</b>: Paper mandates are used</p>
				<p>
					<b>Direct Debit Setup</b>: Each member is configured with a schedule for 12 payments, which are collected monthly, on the 15th or the next business day.</p>
			</td>
			<td>
				<ol>
					<li value="1">When a paper mandate is received, the details are reviewed to ensure they are correct.</li>
					<li value="2">Use <a href="np_createmandate.html">Create Mandate</a> to set up your mandate; it is created in Active status. </li>
					<li value="3">Use <a href="np_createschedule.html">Create Payment Schedule</a> to link a schedule to the mandate in step 2; payments are collected on the 15th of each month.</li>
					<li value="4">Optionally you can use <a href="np_listdirectdebits.html">List Direct Debits</a> to view the list of Direct Debit payments linked to the schedule created in step 2.</li>
				</ol>
			</td>
			<td>
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
                    </div>
                   




{% include links.html %}
