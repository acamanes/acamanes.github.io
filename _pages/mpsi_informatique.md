---
layout: single
title: L'Option Informatique en MPSI
permalink: /mpsi/option_informatique.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
toc_icon: "infinity"
sidebar:
  nav: "mpsi"
---

{% assign cptnp = 1 %}

<center>
<nobr>
{% for r in site.data.mpsi_informatique_option.ref %}
<a href="./mpsi_doc/ref/{{r.ref}}" class="ref">&Sigma;</a>
{% endfor %}
</nobr>
</center>


<!-- <a href="{{site.data.psi_info.formulaire}}">Formulaire</a> disponible lors des Oraux de Centrale. -->

<ul start="0" style="list-style-type:none">
{% for chap in site.data.mpsi_informatique_option.presentations %}
{% if cptnp < 10 %}
{% assign np = "0" | append:cptnp %}
{% else %}
{% assign np = cptnp %}
{% endif %}
<li> <h3 id="#p_{{np}}">{{chap.titre}}
{% if chap.ref %}
<a href="./mpsi_doc/ref/{{chap.ref}}" class="ref">&Sigma;</a>
{% endif %}</h3>
<a href="./mpsi_doc/info_option/oi-p_{{np}}.pdf">Présentation</a>.
{% if chap.td %}
<a href="./mpsi_doc/info_option/oi-td_e{{np}}.pdf">T.D.</a>.
{% endif %}
</li>
{% assign cptnp = cptnp | plus:1 %}
{% endfor %}
</ul>
