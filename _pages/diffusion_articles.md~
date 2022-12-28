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

<center>
<nobr>
{% for r in site.data.diffusion_ateliers.ref %}
<a href="./psi_doc/ref/{{r.ref}}" class="ref">&Sigma;</a>
{% endfor %}
</nobr>
</center>

{{site.data.diffusion_ateliers.presentation}}

{% for chap in site.data.diffusion_ateliers.ateliers %}
<h2 id="#docs_{{cptdoc}}">{{chap.titre}}
{% if chap.niveau %}
({{chap.niveau}}) 
{% endif %}
</h2>
{{chap.presentation}}
{% if chap.ateliers %}
<ul>
{% for doc in chap.ateliers %}
<li>{{doc.titre}}
{% if doc.niveau %}
({{doc.niveau}})
{% endif %}
<br/><a href="{{doc.fichier}}.pdf">Fiche professeur</a>, <a href="{{doc.fichier}}.zip">Ressources</a>.
</li>
{% endfor %}
</ul>
{% else %}
<a href="{{chap.fichier}}.pdf">Fiche professeur</a>, <a href="{{chap.fichier}}.zip">Ressources</a>.
{% endif %}
{% endfor %}
