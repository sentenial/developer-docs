---
title: FAQs
permalink: ob_faq.html
sidebar: ob_sidebar
keywords: frequently asked questions, FAQ, question and answer Open Banking
summary: "Frequently Asked Questions have been provided here and arranged based on various Open Banking  areas."
toc: false
folder: prodNuapay
---

<h2>Configuration</h2>

<div class="panel-group" id="accordion">
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseOne">How do I get set up to test Open Banking?</a>
                            </h4>
                        </div>
                        <div id="collapseOne" class="panel-collapse collapse noCrossRef">
                            <div class="panel-body">
                                <p>To get set up on the system:</p>
                                                <ol>
                                                    <li value="1">Contact our support team: <a href="mailto:api.support@sentenial.com?subject=Nuapay -- Sandbox Request">api.support@nuapay.com</a></li>
                                                    <li value="2">Provide us with some basic details (your name, business area, etc.)</li>
                                                    <li value="3">We'll register you and send you the following:<ul><li value="1">An API Key</li><li value="2">A test Merchant account</li><li value="3">A link to our testing environment</li></ul></li>
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
                            <p>When you register for the service you may optionally receive a Nuapay IBAN. This account will  be used to receive all Open Banking payments you generate. Note that if you want to use the <a href="ob_reversepayment.html">Reverse Payment</a> service you must have a Nuapay account. </p>

                            
                            </div>
                        </div>
                    </div>
                    

<h2>Some Key Concepts</h2>

                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseFour">What is a PSU?</a>
                            </h4>
                        </div>
                        <div id="collapseFour" class="panel-collapse collapse">
                            <div class="panel-body">
                               <p>A PSU is a Payment Services User. This is the end user who interacts with the Nuapay TPP. A PSU can act as a payer, a payee or both. When working with the Nuapay PISP the PSU is a payer when a payment is created. If that user is later refunded, via the Reverse Payment service, the PU becomes a payee. </p>

                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseFive">What is a TPP?</a>
                            </h4>
                        </div>
                        <div id="collapseFive" class="panel-collapse collapse">
                            <div class="panel-body">
                            <p>A TPP is a Third Party Provider of open Banking services. Nuapay is a TPP and offers both payment and account services via our APIs to merchants and their PSUs.</p>
                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseSix">What is the ASPSP?</a>
                            </h4>
                        </div>
                        <div id="collapseSix" class="panel-collapse collapse">
                            <div class="panel-body">
                            <p>An ASPSP is an Account Servicing Payment Service Provider. This is the institiution that holds and maintains the bank accounts of PSUs. In Open Banking terms the ASPSP publish APIs that allow TPPs to connect to clients' bank accounts allowing TPPS to provision account and payment services.</p>
                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse7">What is a PISP service?</a>
                            </h4>
                        </div>
                        <div id="collapse7" class="panel-collapse collapse">
                            <div class="panel-body">
                            <p>A Payment Initiation Services Provider service allows merchants to provide online payment initiation services for their payment service users. In the Nuapay TPP our PISP services allow you to offer an Open Banking payment flow from your Payment Page. </p>
                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse8">What is an AISP service?</a>
                            </h4>
                        </div>
                        <div id="collapse8" class="panel-collapse collapse">
                            <div class="panel-body">
                            <p>An AISP (Account Information Service Provider) service is a TPP-provided service that allows merchants to access sepecific bank account data of its clients. This access may be used to provide consolidated information on one or more accounts held by a PSU with one or more payment service provider(s), for exam.</p>
                            </div>
                        </div>
                    </div>
<h2>Technical</h2>                    
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse9">Do I need a User Name & Password when accessing a Nuapay Open Banking API?</a>
                            </h4>
                        </div>
                        <div id="collapse9" class="panel-collapse collapse">
                            <div class="panel-body">
                                <p>No but you will need to be authorised with a Base64-encoded API Key. See <a href="ob_generalrules.html"> General API Rules</a> for more.</p>
                                
                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse10">What happens when a user closes the PISP pop-up window?</a>
                            </h4>
                        </div>
                        <div id="collapse10" class="panel-collapse collapse">
                            <div class="panel-body">
                            <p>You will need to know the final status of the Open Banking payment. You should manage this by ensuring that you make a <a href="ob_retrievepayment.html">Retrieve Payment</a> request whenever the pop-window is closed and control is passed back to the parent window.</p>
                            </div>
                        </div>
                    </div>
                    <!-- /.panel -->
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse11">I want to retry an Open Banking payment - is there a risk of duplication?</a>
                            </h4>
                        </div>
                        <div id="collapse11" class="panel-collapse collapse">
                            <div class="panel-body">
                            <p>We recommend that you use the x-idempotency-key Header parameter in all your Create Payment requests.</p>

                         
                            </div>
                        </div>
                    </div>                   
                    <!-- /.panel -->
</div>
<!-- /.panel-group -->

{% include links.html %}
