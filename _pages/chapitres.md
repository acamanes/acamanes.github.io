---
layout: single
title: Les Chapitres en PSI
permalink: /psi/
---

<ol start="0">
{% for chap in site.chapters %}
<li>{{chap.titre}}
{% if chap.chapitre %}
<a href="./psi_doc/chap_e{{chap.number}}.pdf">Cours</a>,
{% endif %}


{% if chap.td %}
<a href="./psi_doc/exos_e{{chap.number}}.pdf">Exercices</a>,
{% endif %}


{% if chap.tdindic %}
<a href="./psi_doc/exos_i{{chap.number}}.pdf">Indications</a>,
{% endif %}

{% if chap.themes %}
<p> Thèmes <ul>
{% for th in chap.themes %}
<li>
<a href="./psi_doc/themes_e{{th.number}}.pdf">{{th.titre}}</a>
</li>
{% endfor %}
</ul></p>
{% endif %}
</li>
{% endfor %}
</ol>
