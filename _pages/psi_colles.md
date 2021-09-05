---
layout: single
title: Les Colles en PSI
permalink: /psi/colles.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 6
---


{% assign week = 7 | times: 86400 %}
{% assign 4jours = 4 | times: 86400 %}

{% assign debutsemaine = site.data.psi_colles.startdate | date : "%s" %}
{% assign finsemaine = site.data.psi_colles.startdate | date : "%s" | plus: 4jours | date: "%s" %}

<ol>
{% for s in site.data.psi_colles.semaines %}
{% if s.holidays != true %}
<li>
<h6>{{debutsemaine| date:"%d/%m"}}-{{finsemaine| date:"%d/%m"}}</h6>
<a href="./psi_doc/colle{{s.number}}.pdf">{{s.title}}</a>
</li>
{% else %}
{{s.title}}
{% endif %}

{% assign debutsemaine = debutsemaine | date : "%s" | plus: week %}
{% assign finsemaine = finsemaine | date : "%s" | plus: week %}
{% endfor %}
</ol>
