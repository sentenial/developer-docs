---
title: Verification Scoring
keywords: Verification scoring
summary: "Once the account holder name is retrieved from the bank, a matching score is calculated."
sidebar: ver_sidebar
permalink: ver_scoring.html
folder: prodNuapay
toc: false
---
## Overview

To determine a matching score:
* When the account holder name is retrieved from the bank, it is compared to the name passed in the original `POST /verification` request.
* A score is calculated, which may be returned in the response to `GET /verification/{verificationId}` endpoint. Pass the verification `id` returned in the `POST /verification` response.
* Scores are returned in the range 0 to 100 with 0 being unmatched and 100% being treated as an exact match.

## Scoring Logic

Nuapay uses a specific algorithm to determine the matching score.
It is up to clients to decide on how to proceed, based on the score returned.

## Scoring Examples
The following table gives some examples of how the provided name versus the account holder name returned from the bank might be handled.

{% include tip.html content="It is up to the client to decide on how to proceed based on the returned score." %}

<table border=1 cellspacing=0 cellpadding=0 width = "100%" style='border-collapse:
 collapse;border:none'>
 <tr>
  <td width=62 valign=top style='width:46.25pt;border:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'><b>Score</b></p>
  </td>
  <td width=89 valign=top style='width:66.9pt;border:solid windowtext 1.0pt;
  border-left:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'><b>Result</b></p>
  </td>
  <td width=255 valign=top style='width:191.4pt;border:solid windowtext 1.0pt;
  border-left:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'><b>Example</b></p>
  </td>
  <td width=160 valign=top style='width:120.2pt;border:solid windowtext 1.0pt;
  border-left:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'><b>Client Decision</b></p>
  </td>
 </tr>
 <tr>
  <td width=62 valign=top style='width:46.25pt;border:solid windowtext 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'>100</p>
  </td>
  <td width=89 valign=top style='width:66.9pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'>Exact Match</p>
  </td>
  <td width=255 valign=top style='width:191.4pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <table class=MsoTableGrid border=1 cellspacing=0 cellpadding=0
   style='border-collapse:collapse;border:none'>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>&nbsp;</p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border:solid windowtext 1.0pt;
    border-left:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>Name Provided/Retrieved </b></p>
    </td>
   </tr>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>Verification Request:</b></p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border-top:none;border-left:
    none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>John Smith</p>
    </td>
   </tr>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>AIS Response:</b></p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border-top:none;border-left:
    none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>John Smith</p>
    </td>
   </tr>
   <tr>
    <td width=221 colspan=2 valign=top style='width:165.9pt;border:solid windowtext 1.0pt;
    border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>OR</p>
    </td>
   </tr>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>Verification Request</b></p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border-top:none;border-left:
    none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>Tommy Adams</p>
    </td>
   </tr>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>AIS Response:</b></p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border-top:none;border-left:
    none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>Thomas Adams</p>
    </td>
   </tr>
  </table>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'></p>
  </td>
  <td width=160 valign=top style='width:120.2pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'>The client can be
  confident that there is a match where names match exactly.</p>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'>In the second
  example, the algorithm sees “Tommy” and “Thomas” as being essentially a match
  so 100 is returned as the score here too.</p>
  </td>
 </tr>
 <tr>
  <td width=62 valign=top style='width:46.25pt;border:solid windowtext 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'>0</p>
  </td>
  <td width=89 valign=top style='width:66.9pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'>No Match</p>
  </td>
  <td width=255 valign=top style='width:191.4pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <table class=MsoTableGrid border=1 cellspacing=0 cellpadding=0
   style='border-collapse:collapse;border:none'>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>&nbsp;</p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border:solid windowtext 1.0pt;
    border-left:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>Name Provided/Retrieved </b></p>
    </td>
   </tr>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>Verification Request:</b></p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border-top:none;border-left:
    none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>John Smith</p>
    </td>
   </tr>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>AIS Response:</b></p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border-top:none;border-left:
    none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>Susan Jones</p>
    </td>
   </tr>
  </table>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'></p>
  </td>
  <td width=160 valign=top style='width:120.2pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'>The names do not
  match.</p>
  </td>
 </tr>
 <tr>
  <td width=62 valign=top style='width:46.25pt;border:solid windowtext 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'>43</p>
  </td>
  <td width=89 valign=top style='width:66.9pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'>Partial Match</p>
  </td>
  <td width=255 valign=top style='width:191.4pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <table class=MsoTableGrid border=1 cellspacing=0 cellpadding=0
   style='border-collapse:collapse;border:none'>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>&nbsp;</p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border:solid windowtext 1.0pt;
    border-left:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>Name Provided/Retrieved </b></p>
    </td>
   </tr>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>Verification Request:</b></p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border-top:none;border-left:
    none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>John Smith</p>
    </td>
   </tr>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>AIS Response:</b></p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border-top:none;border-left:
    none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>John Smyth</p>
    </td>
   </tr>
  </table>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'></p>
  </td>
  <td width=160 valign=top style='width:120.2pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'>The client will need
  to review; in this example, the client would treat this result as non-matching,
  as the surnames are different.</p>
  </td>
 </tr>
 <tr>
  <td width=62 valign=top style='width:46.25pt;border:solid windowtext 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'>86</p>
  </td>
  <td width=89 valign=top style='width:66.9pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'>Partial Match</p>
  </td>
  <td width=255 valign=top style='width:191.4pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <table class=MsoTableGrid border=1 cellspacing=0 cellpadding=0
   style='border-collapse:collapse;border:none'>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>&nbsp;</p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border:solid windowtext 1.0pt;
    border-left:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>Name Provided/Retrieved </b></p>
    </td>
   </tr>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>Verification Request:</b></p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border-top:none;border-left:
    none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>Thalia Jones</p>
    </td>
   </tr>
   <tr>
    <td width=90 valign=top style='width:67.8pt;border:solid windowtext 1.0pt;
    border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'><b>AIS Response:</b></p>
    </td>
    <td width=131 valign=top style='width:98.1pt;border-top:none;border-left:
    none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
    padding:0cm 5.4pt 0cm 5.4pt'>
    <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
    3.0pt;margin-left:0cm;line-height:normal'>Natalia Jones Smith</p>
    </td>
   </tr>
  </table>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'></p>
  </td>
  <td width=160 valign=top style='width:120.2pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm;line-height:120%'>The client will need
  to review; in this example, the client might decide that the similarity in
  names is enough to confirm a match.</p>
  </td>
 </tr>
</table>



{% include links.html %}
