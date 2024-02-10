---
layout: page
permalink: /gradieNTAG/
title: gradieNTAG
description: the SFU graduate student seminar in number theory and algebraic geometry (gradieNTAG)
nav: true
nav_order: 4
custom_header: true
header_title: ∇NTAG
---

You can find the schedule of our graduate student seminar below. If you are a student at SFU or are visiting SFU and would like to give a talk at gradieNTAG, please contact me (`ahmad_mokhtar at sfu dot ca`) or Sharon Robins (`srobins at sfu dot ca`) or Pijush Sarmah (`pps3 at sfu dot ca`). If you are looking for the SFU Number Theory and Algebraic Geometry (NTAG) seminar, it is <a href='http://www.cecm.sfu.ca/~nbruin/NTAG/'>here</a>.

<table class="styled-table">
  {% assign gradientag-data = site.data.gradientag %}
  <tr>
      {% for heading in gradientag-data.headings %}
        <th>{{ heading.string }}</th>
      {% endfor %}
  </tr>

  {% for talk in gradientag-data.talks %}
    <tr>
    {% for heading in gradientag-data.headings %}
      <td>
        {% if talk.abstract and heading.title=="title" %}
          <div class="collapsible">{{ talk[heading.title] }}</div>
          <div class="content">
            <p><b>Abstract: </b>{{ talk.abstract }}</p>
          </div>
        {% else %}
          {{ talk[heading.title] }}
        {% endif %}
      </td>
    {% endfor %}
    </tr>
  {% endfor %}
</table>

<script>
var coll = document.getElementsByClassName("collapsible");
var i;

for (i = 0; i < coll.length; i++) {
  coll[i].addEventListener("click", function() {
    this.classList.toggle("active");
    var content = this.nextElementSibling;
    if (content.style.display === "block") {
      content.style.display = "none";
    } else {
      content.style.display = "block";
    }
  });
}
</script>
