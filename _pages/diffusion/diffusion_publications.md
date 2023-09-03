---
layout: single
title: Livres & Articles publiés
permalink: /diffusion/publications.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
toc_icon: "infinity"
sidebar:
  nav: "diffusion"
---

{% assign cptdoc = 0 %}

<h2 id="#docs_00"> Livres </h2>
{% for chap in site.data.diffusion.diffusion_articles.livres %}
<h3 id="#docs_{{cptdoc}}">
<a href="{{chap.url}}">
{{chap.titre}}</a>
</h3>
{% if chap.journal %}<i>{{chap.journal}}</i>{% endif %}
<br />
{{chap.presentation}}
{% assign cptdoc = cptdoc  | plus:1 %}
{% endfor %}


<h2 id="#docs_01"> Articles </h2>
{% for chap in site.data.diffusion.diffusion_articles.articles %}
<h3 id="#docs_{{cptdoc}}">{% if chap.fichier %}
<a href="./articles/{{chap.fichier}}">
{% else %}
<a href="{{chap.url}}">
{% endif %}
{{chap.titre}}</a>
</h3>
{% if chap.journal %}<i>{{chap.journal}}</i><br />{% endif %}
{{chap.presentation}}
{% assign cptdoc = cptdoc  | plus:1 %}
{% endfor %}
