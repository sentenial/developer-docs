---
title: Bank Overview
keywords: Open Banking Participating Banks Overview
summary: "The Bank APIs allow you to retrieve and view details of all available banks (ASPSPs)"
sidebar: ob_sidebar
permalink: ob_bankoverview.html
folder: prodOpenBanking
toc: false
---

When making a payment, <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.psu}}">PSUs</a> must initially select the <a href="#" data-toggle="tooltip" data-original-title="{{site.data.glossary.aspsp}}">ASPSP</a> with which their account is held.

* In [CHECKOUT](ob_pispimplementations.html#implementation-overview) and [REDIRECT](ob_pispimplementations.html#implementation-overview) modes the list of banks is displayed automatically.
* In [SELF-HOSTED](ob_pispimplementations.html#implementation-overview) and [SELF-HOSTED-CALLBACK](ob_pispimplementations.html#implementation-overview) mode, you will need to call [Retrieve Banks](ob_getbank.html) to get the list of banks that you want to display to your PSUs on your user interface.

Nuapay supports Open Banking payments in GBP and EUR currencies. Click the country link below to view the banks that are currently available on our Live environment.

## Country Coverage

{% include note.html content="We are constantly building on our connections and currently we have approximately 95% bank coverage on average, in the countries referenced below." %}

**GBP-Supporting Banks**

<div class="panel-group" id="accordion">
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <strong><a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseOne">United Kingdom</a></strong>                                
                            </h4>
                        </div>
                        <div id="collapseOne" class="panel-collapse collapse noCrossRef">
                            <div class="panel-body">

                            {% include ob_uk_bnks.html %}

                            </div>
                        </div>
                    </div>
                  </div>
**EUR-Supporting Banks**
<div class="panel-group" id="accordion">
                    <!-- /.panel -->                    
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <strong><a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseTwo">Belgium</a></strong>
                            </h4>
                        </div>
                        <div id="collapseTwo" class="panel-collapse collapse noCrossRef">
                        <div class="panel-body">                

                          {% include ob_be_banks.html %}

                            </div>
                        </div>
                    </div>

                    <!-- /.panel -->                    
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <strong><a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseThree">France</a></strong>
                            </h4>
                        </div>
                        <div id="collapseThree" class="panel-collapse collapse noCrossRef">
                        <div class="panel-body">

                        {% include ob_fr_bnks.html %}



                            </div>
                        </div>
                    </div>

                    <!-- /.panel -->                    
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <strong><a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseFour">Germany</a></strong>
                            </h4>
                        </div>
                        <div id="collapseFour" class="panel-collapse collapse noCrossRef">
                        <div class="panel-body">

                        {% include ob_de_bnks.html %}



                            </div>
                        </div>
                    </div>

                    <!-- /.panel -->                    
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <strong><a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseFive">Ireland</a></strong>
                            </h4>
                        </div>
                        <div id="collapseFive" class="panel-collapse collapse noCrossRef">
                        <div class="panel-body">

                        {% include ob_ie_bnks.html %}



                            </div>
                        </div>
                    </div>

                    <!-- /.panel -->                    
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <strong><a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseSix">Italy</a></strong>
                            </h4>
                        </div>
                        <div id="collapseSix" class="panel-collapse collapse noCrossRef">
                        <div class="panel-body">

                        {% include ob_it_bnks.html %}



                            </div>
                        </div>
                    </div>

                    <!-- /.panel -->                    

                    <!-- /.panel -->                    
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <strong><a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseSeven">Netherlands</a></strong>
                            </h4>
                        </div>
                        <div id="collapseSeven" class="panel-collapse collapse noCrossRef">
                        <div class="panel-body">

                        {% include ob_nl_bnks.html %}



                            </div>
                        </div>
                    </div>

                    <!-- /.panel -->                    
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">
                                <strong><a class="noCrossRef accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapseEight">Spain</a></strong>
                            </h4>
                        </div>
                        <div id="collapseEight" class="panel-collapse collapse noCrossRef">
                        <div class="panel-body">

                        {% include ob_es_bnks.html %}



                            </div>
                        </div>
                    </div>
