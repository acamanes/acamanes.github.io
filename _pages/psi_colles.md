---
layout: single
title: Les Colles en PSI
permalink: /psi/colles.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 6
toc_icon: "infinity"
sidebar:
  nav: "psi"
---

{% assign week = 7 | times: 86400 %}
{% assign quatrejours = 4 | times: 86400 %}
{% assign debutsemaine = site.data.psi_colles.startdate | date : "%s" %}
{% assign finsemaine = site.data.psi_colles.startdate | date : "%s" | plus: quatrejours %}
{% assign number = 1 %}

<center>
<nobr>
{% for r in site.data.psi_colles.ref %}
<a href="./psi_doc/ref/{{r.ref}}" class="ref">&Sigma;</a>
{% endfor %}
</nobr>
</center>

<ol>
{% for s in site.data.psi_colles.semaines %}
{% if number < 10 %}
{% assign cpt = "0" | append:number %}
{% else %}
{% assign cpt = number %}
{% endif %}

{% if s.holidays != true %}
<li>
<h6 id="colle_{{cpt}}">{{debutsemaine| date:"%d/%m"}}-{{finsemaine| date:"%d/%m"}}</h6>
<a href="./psi_doc/colle{{cpt}}.pdf">{{s.title}}</a>
</li>
{% assign number = number | plus: 1 %}
{% else %}
{{s.title}}
{% endif %}

{% assign debutsemaine = debutsemaine | date : "%s" | plus: week %}
{% assign finsemaine = finsemaine | date : "%s" | plus: week %}
{% endfor %}
</ol>
