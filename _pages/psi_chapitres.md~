---
layout: single
title: Les Chapitres en PSI
permalink: /psi/
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
---

<ul start="0" style="color:Peru; list-style-type:none">
{% for chap in site.chapters %}
<li>

<h2 id="chap_{{chap.number}}" style="color:Peru">{{chap.number}} - {{chap.titre}}</h2>
{% if chap.chapitre %}
<a href="./psi_doc/chap_e{{chap.number}}.pdf">Cours</a>,
{% endif %}


{% if chap.td %}
<a href="./psi_doc/exos_e{{chap.number}}.pdf">Exercices</a>,
{% endif %}


{% if chap.tdindic %}
<a href="./psi_doc/exos_i{{chap.number}}.pdf">Indications</a>,
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
<li>
<a href="./psi_doc/themes_e{{th.number}}.pdf">{{th.titre}}</a>
</li>
{% endfor %}
</ul>
{% endif %}
</li>
{% endfor %}
</ul>
