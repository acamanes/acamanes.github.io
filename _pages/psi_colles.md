---
layout: single
title: Les Colles en PSI
permalink: /psi/colles.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
---


{% assign week = 7 | times: 24 | times: 60 | times: 60 %}
{% assign jours = 4 | times: 24 | times: 60 | times: 60 %}

{% assign debutsemaine = site.data.psi_colles.startdate | date : "%d/%m/%Y" %}
{% assign finsemaine = site.data.psi_colles.startdate | date : "%s" | plus: jours | date: "%d/%m/%Y" %}

<ol>
{% for s in site.data.psi_colles.semaines %}
{% if s.holidays != true %}
<li>
{{debutsemaine| date:"%d/%m"}}-{{finsemaine| date:"%d/%m"}}
<a href="./psi_doc/colle{{s.number}}.pdf">{{s.title}}</a>
</li>
{% else %}
{{s.title}}
{% endif %}
{% assign debutsemaine = debutsemaine | date : "%s" | plus: week | date: "%d/%m/%Y" %}
{% assign finsemaine = finsemaine | date : "%s" | plus: week | date: "%d/%m/%Y" %}
{% endfor %}
</ol>
