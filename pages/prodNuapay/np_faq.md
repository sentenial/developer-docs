---
title: FAQs
permalink: np_faq.html
sidebar: np_sidebar
keywords: frequently asked questions, FAQ, question and answer
summary: "Frequently Asked Questions have been provided here and arranged based on various Nuapay areas."
toc: false
folder: prodNuapay
---

<h2> My Nuapay Configuration</h2>

<div class="panel-group" id="accordion">
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseOne">How do I get set up to test Nuapay?</a>
                            </h4>
                        </div>
                        <div id="collapseOne" class="panel-collapse collapse noCrossRef">
                            <div class="panel-body">
                                <p>To get set up on the system:</p>
                                                <ol>
                                                    <li value="1">Contact our support team: <a href="mailto:api.support@sentenial.com?subject=Nuapay -- Sandbox Request">api.support@nuapay.com</a></li>
                                                    <li value="2">Provide us with some basic details (your name, business area, etc.)</li>
                                                    <li value="3">We'll register you and send you the following:<ul><li value="1">An API Key</li><li value="2">A test Creditor Scheme ID</li><li value="3">A test Merchant account</li><li value="4">A link to our testing environment</li></ul></li>
                                                </ol>

                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseTwo">What is a Nuapay Account?</a>
                            </h4>
                        </div>
                        <div id="collapseTwo" class="panel-collapse collapse noCrossRef">
                            <div class="panel-body">
                            <p>When you register for the service you will be assigned a Nuapay IBAN. This is a virtual account that you will use as your merchant account when processing mandates and Direct Debit payments.</p>

                            <p>When you make direct debit settlements the funds you collect are initially credited to this virtual IBAN. On the settlement date the funds are then debited from this account and credited to your physical (real-world account) via a Credit Transfer. This is automatically handled by Nuapay in the majority of cases but may be manually manged by you if required - please discuss the available options with you Account Manager.</p>
                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseThree">How are Fees Handled?</a>
                            </h4>
                        </div>
                        <div id="collapseThree" class="panel-collapse collapse noCrossRef">
                            <div class="panel-body">
                                 <p>Fees may be taken from each collection or you may opt to have your fees handled outside of the settlement cycle. </p>
                                                <p>If you want fees to be taken from each settlement cycle, your credit would be calculated like this for a given settlement date:</p>
                                                <ul>
                                                    <li value="1">Credit (10 transactions): €100</li>
                                                    <li value="2">Rejects: €10</li>
                                                    <li value="3">Fee for Transaction: €1</li>
                                                    <li value="4">Fee for Reject: €2</li>
                                                    <li value="5">Credit Due on settlement date: €87</li>
                                                </ul>
                                                <p>Alternatively fees may be charged separately and collected monthly. In this model your payments would be handled like this:</p>
                                                <ul>
                                                    <li value="1">Credit (10 transactions): €100</li>
                                                    <li value="2">Rejects: €10</li>
                                                    <li value="3">Credit Due on settlement date: €90</li>
                                                </ul>
                                                <p>Your fees (€3) would then be charged to you separately with this amount being deducted from your nominated account on the 14th of the following month. </p>
                                                <p>If you want to have your fees handled like this you will need to sign a mandate with Nuapay so that we can collect your fees via Direct Debit each month.</p>
                            </div>
                        </div>
                    </div>

<h2>Mandates</h2>

                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseFour">I have modified a mandate - Why is it now in Pending status?</a>
                            </h4>
                        </div>
                        <div id="collapseFour" class="panel-collapse collapse">
                            <div class="panel-body">
                               <p>If you have modified a mandate and altered key mandate details you may need to re-send it to your payer for authorisation; Nuapay will set the mandate to Pending automatically. If not dispatched for re-signature your payer could contest a debit from his/her account and argue that authorisation was never provided.</p>

                                <p>If you require that your mandate should remain in Active status you can set the mandateInfo.resendMandateForSignature flag to DO_NOT_SEND (see <a href="np_updatemandate.html">Update Mandate</a> for more on this).</p>
                                <p><b>NOTE</b>: If the mandate is currently in Pending status and you want to activate it, use <a href="np_activatemandate.html">Activate Mandate</a>.</p>

                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseFive">Can I cancel all payments linked to a mandate but re-use the mandate later?</a>
                            </h4>
                        </div>
                        <div id="collapseFive" class="panel-collapse collapse">
                            <div class="panel-body">
                            <p>  When you cancel a mandate all Direct Debit payments linked to that mandate are cancelled. The mandate cannot be reused. If you want to cancel all the payments in a fixed-length schedule but still be able to use the mandate later, use Revoke All Direct Debits.</p>

                            <p><b>Note</b>: For an open-ended schedule this operation will only revoke the current READY FOR EXPORT payment, a new payment will be added automatically based on the payment frequency defined. For an open-ended schedule use the <a href="np_cancelschedule.html">Cancel Payment Schedule</a> service.</p>
                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseSix">What is a Suspended Mandate?</a>
                            </h4>
                        </div>
                        <div id="collapseSix" class="panel-collapse collapse">
                            <div class="panel-body">
                            <p>When a mandate is suspended all its linked Direct Debits are put into cancelled status. Unlike a cancel operation, a mandate that is suspended may be re-activated later.</p>

                            <p><b>Note</b>: It is not currently possible to suspend a mandate via the API but this can be done via the Nuapay user interface.</p>
                            </div>
                        </div>
                    </div>
<h2>Direct Debit Payments</h2>                    
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseSeven">What is the Collection Date?</a>
                            </h4>
                        </div>
                        <div id="collapseSeven" class="panel-collapse collapse">
                            <div class="panel-body">
                                <p>The collection date (also referred to as the Settlement Date and the Value Date) is the date on which funds are debited from your payers' bank account and credited to your Nuapay account and (optionally - see the note below) credited from there to your external, non-Nuapay bank account. </p>
                                <p><b>Note</b>: If you are configured as a Self-Managed originator then you control when funds are moved from your Nuapay account; your funds stay on your account until you initiate a funds transfer either via the API or via the Nuapay User Interface. If you are not Self-Managed then your settlement amount is automatically swept to your external account on the collection date.</p>
                                
                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseEight">What are the possible Direct Debit statuses?</a>
                            </h4>
                        </div>
                        <div id="collapseEight" class="panel-collapse collapse">
                            <div class="panel-body">
                            <p>Direct Debit payments are initially created in READY FOR EXPORT status. They move to EXPORTED and then to ACCEPTED, if all goes well. If the transactions is rejected (either before the settlement date or after the settlement date ) then the status may be updated to REJECTED, REFUSED, RETURNED, etc. See <a href= "np_ddstatuses.html">Direct Debit Statuses</a> for more on this</p>
                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseNine">How do Re-presentations work?</a>
                            </h4>
                        </div>
                        <div id="collapseNine" class="panel-collapse collapse">
                            <div class="panel-body">
                            <p>A re-presentation lets you re-try to settle a Direct Debit payment that has been rejected. When you re-present a payment (see <a href="np_representfaileddds.html"> Re-present Failed Direct Debits</a>) the original failed Direct Debit's status is updated to REPRESENTED; this payment is no longer used at this point.</p>

                            <p>A new payment (in READY FOR EXPORT status) is created that attempts to collect the original payment.</p>
                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseTen">Why do I need to use List Failed Direct Debits?</a>
                            </h4>
                        </div>
                        <div id="collapseTen" class="panel-collapse collapse">
                            <div class="panel-body">
                            <p>Direct Debit payments are typically exported 2 days before the collection date. From this point onward debtor banks will begin to process the transactions and you will begin to see a certain portion of payments being rejected.</p>

                        <p>The <a href ="np_listfaileddds.html">List Failed Direct Debits</a> call allows you to track the status of all your failed payments and allows you to manage how best to handle them (you may need to re-present a payment or you may need to contact your payer if an incorrect IBAN has been provided, for example)</p>
                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseEleven">What is a PAIN.008?</a>
                            </h4>
                        </div>
                        <div id="collapseEleven" class="panel-collapse collapse">
                            <div class="panel-body">
                            <p>As per the SEPA standard for Direct Debit processing, payments must be grouped into a standardised ISO format XML file. The standard XLS file this is the PAIN.008.001.02 file (generally referred to as a PAIN.008 or Pain8). This format is used in the Customer-to-Bank space.</p>
                            <p>Prior to their settlement date, all Direct Debit payments are then grouped into PACS.003 files, used in the Bank-to-Bank space, and passed on to Clearing and from there out to all your payers' banks for further processing.</p>
                            </div>
                        </div>
                    </div>
<h2>Failed Payments (R-Transactions)</h2>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseTwelve">What is the difference between a REJECT and a RETURN?</a>
                            </h4>
                        </div>
                        <div id="collapseTwelve" class="panel-collapse collapse">
                            <div class="panel-body">
                            <p>A re-presentation lets you re-try to settle a Direct Debit payment that has been rejected. When you re-present a payment (see <a href="np_representfaileddds.html"> Re-present Failed Direct Debits</a>) the original failed Direct Debit's status is updated to REPRESENTED; this payment is no longer used at this point.</p>

                            <p>A new payment (in READY FOR EXPORT status) is created that attempts to collect the original payment.</p>
                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
</div>
<!-- /.panel-group -->

{% include links.html %}
