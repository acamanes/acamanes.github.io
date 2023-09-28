---
layout: single
title: "Cours & Exercices en D2"
permalink: /d2/chapitres.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
toc_icon: "infinity"
sidebar:
  nav: "d2"
---

{% assign cptfc = 1 %}
{% assign cpthp = 1 %}
{% assign cpttop = 1 %}
{% assign cpttheme = 1 %}

<i>
Les solutions des exercices n'ont pas été suffisamment relues et comportent encore des coquilles. Utilisez les avec un regard critique et n'hésitez pas à me communiquer toute erreur que vous auriez constatée.
</i>

<ul start="0" style="list-style-type:none">
{% for chap in site.data.d2.d2_chapitres.chapitres %}
{% assign number = forloop.index | plus: 0 %}
{% if number < 10 %}
{% assign number = "0" | append:number %}
{% endif %}
<li>
<h2 class="mycss" id="chap_{{number}}">{{number}} - {{chap.titre}}
{% if chap.ref %}
<a href="./ref/{{chap.ref}}" class="ref">&Sigma;</a>
{% endif %}</h2>
{% if chap.chapitre %}
<a href="./chapitres/d2-chap{{number}}.pdf">Cours</a>
{% endif %}

{% if chap.td %},{%else%}.{%endif%}

{% if chap.td %}
<a href="./exercices/d2-exos_e{{number}}.pdf">Exercices</a>
{% endif %}

{% if chap.tdsol %},{%else%}.{%endif%}

{% if chap.tdsol %}
<a href="./exercices/d2-exos_s{{number}}.pdf">Solutions</a>.
{% endif %}
</li>
{% endfor %}
</ul>
