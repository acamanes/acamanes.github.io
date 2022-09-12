---
layout: single
title: "Chapitres en ECT 2"
permalink: /ect2/chapitres.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
toc_icon: "infinity"
sidebar:
  nav: "ect2"
---

{% assign cptfc = 1 %}
{% assign cpthp = 1 %}
{% assign cpttop = 1 %}
{% assign cpttheme = 1 %}

<ul start="0" style="list-style-type:none">
{% for chap in site.data.ect2_chapitres.chapitres %}
{% assign number = forloop.index | plus: 0 %}
{% if number < 10 %}
{% assign number = "0" | append:number %}
{% endif %}
<li>
<h2 class="mycss" id="chap_{{number}}">{{number}} - {{chap.titre}}
{% if chap.ref %}
<a href="./ect2_doc/ref/{{chap.ref}}" class="ref">&Sigma;</a>
{% endif %}</h2>
{% if chap.chapitre %}
<a href="./ect2_doc/ect2-chap{{number}}.pdf">Cours</a>,
{% endif %}

{% if chap.td %}
<a href="./ect2_doc/ect2-exos{{number}}.pdf">Exercices</a>,
{% endif %}

{% if chap.tdindic %}
<a href="./ect2_doc/ect2-exos_i{{number}}.pdf">Indications</a>,
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
<a href="./ect2_doc/ect2-fc{{nfc}}.pdf">{{th.titre}}</a>
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
<a href="./ect2_doc/ect2-top_e{{ntop}}.pdf">{{th.titre}}</a>
</li>
{% assign cpttop = cpttop | plus:1 %}
{% endfor %}
</ul>
{% endif %}

{% if chap.animations %}
<h3>Animations</h3>
<ul>
{% for anim in chap.animations %}
<li>
<a href="./ect2_doc/animations{{anim.url}}" target="_blank">{{anim.titre}}</a>
</li>
{% endfor %}
</ul>
{% endif %}


</li>
{% endfor %}
</ul>
