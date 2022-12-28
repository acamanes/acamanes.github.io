---
layout: single
title: Livres & Articles
permalink: /diffusion/articles.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
toc_icon: "infinity"
sidebar:
  nav: "diffusion"
---

{% assign cptdoc = 0 %}

<center>
<nobr>
{% for r in site.data.diffusion_articles.ref %}
<a href="./psi_doc/ref/{{r.ref}}" class="ref">&Sigma;</a>
{% endfor %}
</nobr>
</center>


<h2> Livres </h2>
{% for chap in site.data.diffusion_articles.livres %}
<h3 id="#docs_{{cptdoc}}">
<a href="{{chap.url}}">
{{chap.titre}}</a>
</h3>
{% if chap.journal %}
<b><i>{{chap.journal}}</i></b>
{% endif %}
{{chap.presentation}}
{% assign cptdoc = cptdoc  | plus:1 %}
{% endfor %}


<h2> Articles </h2>
{% for chap in site.data.diffusion_articles.articles %}
<h3 id="#docs_{{cptdoc}}">
{% if chap.fichier %}
<a href="./articles/{{chap.fichier}}">
{% else %}
<a href="{{chap.url}}">
{% endif %}
{{chap.titre}}</a>
</h3>
{% if chap.journal %}
<b><i>{{chap.journal}}</i></b>
{% endif %}
{{chap.presentation}}
{% assign cptdoc = cptdoc  | plus:1 %}
{% endfor %}
