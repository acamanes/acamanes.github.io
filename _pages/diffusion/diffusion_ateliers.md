---
layout: single
title: Ateliers Scientifiques
permalink: /diffusion/ateliers.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1..6
toc_icon: "infinity"
sidebar:
  nav: "diffusion"
---

{% assign cptdoc = 0 %}

<i style="font-size:95%">{{site.data.diffusion.diffusion_ateliers.presentation}}</i>

{% for chap in site.data.diffusion.diffusion_ateliers.ateliers %}
<h2 id="docs_{{cptdoc}}">{{chap.titre}}
{% if chap.niveau %}
({{chap.niveau}}) 
{% endif %}
</h2>
<i style="font-size:90%">{{chap.presentation}}</i>
{% if chap.ateliers %}
<ul>
{% for doc in chap.ateliers %}
<li>{{doc.titre}}
{% if doc.niveau %}
({{doc.niveau}})
{% endif %}
<p style="font-size:75%">
{% if doc.presentation %}
<i>{{doc.presentation}}</i><br/>
{% endif %}
<a href="./ateliers/{{doc.fichier}}.pdf">Fiche professeur</a>, <a href="./ateliers/{{doc.fichier}}.zip">Ressources</a>.
</p>
</li>
{% endfor %}
</ul>
{% else %}
<nobr><br/>
<i style="font-size:75%"><a href="./ateliers/{{chap.fichier}}.pdf">Fiche professeur</a>, <a href="./ateliers/{{chap.fichier}}.zip">Ressources</a>.</i>
{% endif %}
{% assign cptdoc = cptdoc | plus:1 %}
{% endfor %}
