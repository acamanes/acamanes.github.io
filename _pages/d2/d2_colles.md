---
layout: single
title: Les Colles en d2
permalink: /d2/colles.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 6
toc_icon: "infinity"
sidebar:
  nav: "d2"
---

{% assign week = 7 | times: 86400 %}
{% assign quatrejours = 4 | times: 86400 %}
{% assign debutsemaine = site.data.d2.d2_colles.startdate | date : "%s" %}
{% assign finsemaine = site.data.d2.d2_colles.startdate | date : "%s" | plus: quatrejours %}
{% assign number = 1 %}

<ol>
{% for s in site.data.d2.d2_colles.semaines %}
{% if number < 10 %}
{% assign cpt = "0" | append:number %}
{% else %}
{% assign cpt = number %}
{% endif %}

{% if s.holidays != true %}
<li>
<h6 id="colle_{{cpt}}">{{debutsemaine| date:"%d/%m"}}-{{finsemaine| date:"%d/%m"}}</h6>
<a href="./colles/d2-colles{{cpt}}.pdf">{{s.title}}</a>
</li>
{% assign number = number | plus: 1 %}
{% else %}
<em>{{s.title}}</em>
<br/>
{% endif %}

{% assign debutsemaine = debutsemaine | date : "%s" | plus: week %}
{% assign finsemaine = finsemaine | date : "%s" | plus: week %}
{% endfor %}
</ol>
