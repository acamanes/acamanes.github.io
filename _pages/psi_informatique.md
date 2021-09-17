---
layout: single
title: L'Informatique en PSI
permalink: /psi/informatique.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
toc_icon: "infinity"
sidebar:
  nav: "psi"
---

{% assign cpttp = 0 %}

<center>
<nobr>
{% for r in site.data.psi_info.ref %}
<a href="./psi_doc/ref/{{r.ref}}" class="ref">&Sigma;</a>
{% endfor %}
</nobr>
</center>


<a href="{{site.data.psi_info.formulaire}}">Formulaire</a> disponible lors des Oraux de Centrale.

<ul start="0" style="list-style-type:none">
{% for chap in site.data.psi_info.tp %}
<li> <h3 id="#tp_{{cpttp}}">{{chap.titre}}
{% if chap.ref %}
<a href="./psi_doc/ref/{{chap.ref}}" class="ref">&Sigma;</a>
{% endif %}</h3>
{% if cpttp < 10 %}
{% assign ntp = "0" | append:cpttp %}
{% else %}
{% assign ntp = cpttp %}
{% endif %}
<a href="./psi_doc/info/ipt-tp_e{{ntp}}.pdf">Énoncé</a>.
{% if chap.annexes %}
<a href="./psi_doc/info/ipt-tp_{{ntp}}.zip">Données</a>.
{% endif %}
</li>
{% assign cpttp = cpttp | plus:1 %}
{% endfor %}
</ul>
