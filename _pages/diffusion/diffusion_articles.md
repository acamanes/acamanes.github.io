---
layout: single
title: Notes
permalink: /diffusion/notes.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
toc_icon: "infinity"
sidebar:
  nav: "diffusion"
---

{% assign cptdoc = 0 %}

Quelques articles n'ayant pas fait l'objet d'une publication.

{% for chap in site.data.diffusion.diffusion_notes %}
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
