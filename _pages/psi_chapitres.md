---
layout: single
title: Les Chapitres en PSI
permalink: /psi/chapitres.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
sidebar:
  nav: "psi"
---

{% assign cpttheme = 0 %}

<ul start="0" style="color:Peru; list-style-type:none">
{% for chap in site.data.psi_chapitres.chapitres %}
{% assign number = forloop.index | plus: -1 %}
{% if number < 10 %}
{% assign number = "0" | append:{{number}} %}
{% endif %}
<li>
<h2 id="chap_{{}}" style="color:Peru">{{number}} - {{chap.titre}}</h2>
{% if chap.chapitre %}
<a href="./psi_doc/chap_e{{number}}.pdf">Cours</a>,
{% endif %}


{% if chap.td %}
<a href="./psi_doc/exos_e{{number}}.pdf">Exercices</a>,
{% endif %}


{% if chap.tdindic %}
<a href="./psi_doc/exos_i{{number}}.pdf">Indications</a>,
{% endif %}

{% if chap.cplts %}
<h6 style="color:SteelBlue">Compléments</h6> <ul>
{% for cp in chap.cplts %}
<li>
<a href="./psi_doc/themes_e{{cp.number}}.pdf">{{cp.titre}}</a>
</li>
{% endfor %}
</ul>
{% endif %}

{% if chap.themes %}
<h6 style="color:#5090B4">Thèmes</h6> <ul>
{% for th in chap.themes %}
{% if cpttheme < 10 %}
{% assign ntheme = "0" | append:{{cpttheme}} %}
{% else %}
{% assign ntheme = {{cpttheme}} %}
{% endif %}
<li>
<a href="./psi_doc/themes_e{{ntheme}}.pdf">{{th.titre}}</a>
</li>
{% assign cpttheme = cpttheme | plus:1 %}
{% endfor %}
</ul>
{% endif %}
</li>
{% endfor %}
</ul>
