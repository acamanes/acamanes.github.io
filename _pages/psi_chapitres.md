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

{% assign cptfc = 1 %}
{% assign cpttop = 1 %}
{% assign cpttheme = 1 %}

<ul start="0" style="list-style-type:none">
{% for chap in site.data.psi_chapitres.chapitres %}
{% assign number = forloop.index | plus: -1 %}
{% if number < 10 %}
{% assign number = "0" | append:number %}
{% endif %}
<li>
<h2 class="mycss" id= "chap_{{number}}">{{number}} - {{chap.titre}}</h2>
{% if chap.chapitre %}
<a href="./psi_doc/chap_e{{number}}.pdf">Cours</a>,
{% endif %}


{% if chap.td %}
<a href="./psi_doc/exos_e{{number}}.pdf">Exercices</a>,
{% endif %}


{% if chap.tdindic %}
<a href="./psi_doc/exos_i{{number}}.pdf">Indications</a>,
{% endif %}

{% if chap.fc %}
<h3>Flow Chart</h3> <ul>
{% for th in chap.fc %}
{% if cptfc < 10 %}
{% assign nfc = "0" | append:cptfc %}
{% else %}
{% assign nfc = cptfc %}
{% endif %}
<li>
<a href="./psi_doc/fc{{nfc}}.pdf">{{th.titre}}</a>
</li>
{% assign cptfc = cptfc | plus:1 %}
{% endfor %}
</ul>
{% endif %}


{% if chap.top %}
<h3>Compléments</h3> <ul>
{% for th in chap.top %}
{% if cpttop < 10 %}
{% assign ntop = "0" | append:cpttop %}
{% else %}
{% assign ntop = cpttop %}
{% endif %}
<li>
<a href="./psi_doc/top_e{{ntop}}.pdf">{{th.titre}}</a>
</li>
{% assign cpttop = cpttop | plus:1 %}
{% endfor %}
</ul>
{% endif %}


{% if chap.themes %}
<h3>Thèmes</h3> <ul>
{% for th in chap.themes %}
{% if cpttheme < 10 %}
{% assign ntheme = "0" | append:cpttheme %}
{% else %}
{% assign ntheme = cpttheme %}
{% endif %}
<li>
<a href="./psi_doc/themes_e{{ntheme}}.pdf">{{th.titre}}</a>
</li>
{% assign cpttheme = cpttheme | plus:1 %}
{% endfor %}
</ul>
{% endif %}

{% if chap.animations %}
<h3>Animations</h3>
<ul>
{% for anim in chap.animations %}
<li>
<a href="./psi_doc/animations{{anim.url}}" target="_blank">{{anim.titre}}</a>
</li>
{% endfor %}
</ul>
{% endif %}

{% if chap.hp %}
<h3>Résultats Hors-Programme</h3> <ul>
{% for th in chap.hp %}
{% if cpthp < 10 %}
{% assign nhp = "0" | append:cpthp %}
{% else %}
{% assign nhp = cpthp %}
{% endif %}
<li>
<a href="./psi_doc/hp_e{{nhp}}.pdf">{{th.titre}}</a>
</li>
{% assign cpthp = cpthp | plus:1 %}
{% endfor %}
</ul>
{% endif %}


</li>
{% endfor %}
</ul>
