---
layout: page
permalink: /gradieNTAG/
title: gradieNTAG
description: the SFU graduate student seminar in number theory and algebraic geometry (gradieNTAG)
nav: true
nav_order: 2
---

You can find the schedule of our graduate student seminar below. If you are a student at SFU or are visiting SFU and would like to give a talk at gradieNTAG, please contact me (`ahmad_mokhtar at sfu dot ca`) or Sharon Robins (`srobins at sfu dot ca`). If you are looking for the SFU Number Theory and Algebraic Geometry (NTAG) seminar, it is <a href='http://www.cecm.sfu.ca/~nbruin/NTAG/'>here</a>.

<table class="styled-table">
  {% for row in site.data.gradientag %}
    {% if forloop.first %}
    <tr>
      {% for pair in row %}
        <th>{{ pair[0] }}</th>
      {% endfor %}
    </tr>
    {% endif %}

    {% tablerow pair in row %}
      {{ pair[1] }}
    {% endtablerow %}
  {% endfor %}
</table>
