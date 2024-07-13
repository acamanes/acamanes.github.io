---
layout: single
title: Documents de travail
permalink: /ect2/documents.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
toc_icon: "infinity"
sidebar:
  nav: "ect2"
---

{% assign cptdoc = 0 %}

<ul start="0" style="list-style-type:none">
{% for chap in site.data.ect2.ect2_documents.calculs %}
<li> <h3 id="#docs_{{cptdoc}}">{{chap.titre}}</h3>
<ul>
{% for doc in chap.docs %}
<li><a href="./doc/{{doc.url}}">{{doc.titre}}</a>.
</li>
{% endfor %}
</ul>
</li>
{% assign cptdoc = cptdoc | plus:1 %}
{% endfor %}
</ul>
