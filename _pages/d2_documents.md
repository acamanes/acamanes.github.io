---
layout: single
title: Documents de travail
permalink: /d2/documents.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
toc_icon: "infinity"
sidebar:
  nav: "d2"
---

{% assign cptdoc = 0 %}

<center>
<nobr>
{% for r in site.data.d2_documents.ref %}
<a href="./d2_doc/ref/{{r.ref}}" class="ref">&Sigma;</a>
{% endfor %}
</nobr>
</center>

<ul start="0" style="list-style-type:none">
{% for chap in site.data.d2_documents.calculs %}
<li> <h3 id="#docs_{{cptdoc}}">{{chap.titre}}</h3>
<ul>
{% for doc in chap.docs %}
<li><a href="./d2_doc/{{doc.url}}">{{doc.titre}}</a>.
{% for r in doc.ref %}
<a href="./d2_doc/ref/{{r}}" class="ref">&Sigma;</a>
{% endfor %}
</li>
{% endfor %}
</ul>
</li>
{% assign cptdoc = cptdoc | plus:1 %}
{% endfor %}
</ul>
