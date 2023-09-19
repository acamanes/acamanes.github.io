---
layout: single
title: T.P. en ECT 2
permalink: /ect2/informatique.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
toc_icon: "infinity"
sidebar:
  nav: "ect2"
---

{% assign cptnp = 1 %}

<ul start="0" style="list-style-type:none">
{% for chap in site.data.ect2.ect2_informatique.presentations %}
{% if cptnp < 10 %}
{% assign np = "0" | append:cptnp %}
{% else %}
{% assign np = cptnp %}
{% endif %}
<li> <h3 id="#p_{{np}}">{{chap.titre}}
{% if chap.ref %}
<a href="./ref/{{chap.ref}}" class="ref">&Sigma;</a>
{% endif %}</h3>
{% if chap.td %}
<a href="./info/ect2-tp_e{{np}}.pdf">T.D.</a>
{% if chap.sol %}
, <a href="./info/ect2-tp_s{{np}}.pdf">correction</a>
{% endif %}.
{% endif %}
</li>
{% assign cptnp = cptnp | plus:1 %}
{% endfor %}
</ul>
