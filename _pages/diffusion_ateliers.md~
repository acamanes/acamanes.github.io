---
layout: single
title: Documents de travail
permalink: /psi/documents.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
toc_icon: "infinity"
sidebar:
  nav: "psi"
---

{% assign cptdoc = 0 %}

<center>
<nobr>
{% for r in site.data.psi_documents.ref %}
<a href="./psi_doc/ref/{{r.ref}}" class="ref">&Sigma;</a>
{% endfor %}
</nobr>
</center>

<ul start="0" style="list-style-type:none">
{% for chap in site.data.psi_documents.calculs %}
<li> <h3 id="#docs_{{cptdoc}}">{{chap.titre}}</h3>
<ul>
{% for doc in chap.docs %}
<li><a href="{{doc.url}}">{{doc.titre}}</a>.</li>
{% endfor %}
</ul>
</li>
{% assign cptdoc = cptdoc | plus:1 %}
{% endfor %}
</ul>
