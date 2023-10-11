---
layout: single
title: "Cours & Exercices en ECT 2"
permalink: /ect2/chapitres.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
toc_icon: "infinity"
sidebar:
  nav: "ect2"
---

{% assign cptchap = 2 %}
{% assign cpttd = 1 %}
{% assign cptobj = 1 %}
{% assign cptcplts = 1 %}

<i>
Les solutions des exercices n'ont pas été suffisamment relues et comportent encore des coquilles. Utilisez les avec un regard critique et n'hésitez pas à me communiquer toute erreur que vous auriez constatée.
</i>

<ul start="0" style="list-style-type:none">
{% for chap in site.data.ect2.ect2_chapitres.chapitres %}
 {% assign number = forloop.index | plus: -1 %}
 {% if number < 10 %}
  {% assign number = "0" | append:number %}
 {% endif %}

 <li>
 <h2 class="mycss" id="chap_{{number}}">{{number}} - {{chap.titre}}
 </h2>
  {% if chap.chapitre %}
   {% if cptchap < 10 %}
    {% assign nchap = "0" | append:cptchap %}
    {% else %}
    {% assign nchap = cptchap %}
   {% endif %}
   <a href="./chapitres/ect2-chap{{nchap}}.pdf">Cours</a>
   {% if chap.td or chap.tdsol or chap.objectifs %}, {%else%}. {%endif%}
   {% assign cptchap = cptchap | plus:1 %}
  {% endif %}

 {% if chap.td %}
  {% if cpttd < 10 %}
   {% assign ntd = "0" | append:cpttd %}
   {% else %}
   {% assign ntd = cpttd %}
  {% endif %}
   <a href="./exercices/ect2-exos_e{{ntd}}.pdf">Exercices</a>
  {% assign cpttd = cpttd | plus:1 %}
  {% if chap.tdsol or chap.objectifs%},{%else%}.{%endif%}
 {% endif %}


 {% if chap.tdsol %}
   <a href="./exercices/ect2-exos_s{{number}}.pdf">Solutions</a>
   {% if chap.objectifs %}, {%else%}. {%endif%}
 {% endif %}


 {% if chap.objectifs %}
  {% if cptobj < 10 %}
   {% assign nobj = "0" | append:cptobj %}
   {% else %}
   {% assign nobj = cptobj %}
  {% endif %}
 <a href="./objectifs/ect2-objectifs{{nobj}}.pdf">Objectifs</a>.
 {% assign cptobj = cptobj | plus:1 %}
 {% endif %}

 {% if chap.complements %}
 <ul>
 {% for theme in chap.complements %}
  <li>
  {% if cptcplts < 10 %}
    {% assign ncplts = "0" | append:cptcplts %}
    {% else %}
    {% assign ncplts = cptcplts %}
   {% endif %}
   <a href="./complements/ect2-cplts_e{{ncplts}}.pdf">{{theme.titre}}</a>
   {% if theme.sol %}, {% else %}.{% endif %}
   {% if theme.sol %}
    <a href="./complements/ect2-cplts_s{{ncplts}}.pdf">solutions</a>.
   {% endif %}
   {% assign cptcplts = cptcplts | plus:1 %}
  </li>
  {% endfor %}
 </ul>
 {% endif %}
{% endfor %}