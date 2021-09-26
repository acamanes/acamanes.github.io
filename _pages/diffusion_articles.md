---
layout: single
title: Articles Scientifiques
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

{% for chap in site.data.diffusion_articles.articles %}
<h3 id="#docs_{{cptdoc}}"><a href="{{doc.fichier}}.pdf">{{chap.titre}}</a>
</h3>
{{chap.presentation}}
<br/><a href="{{doc.fichier}}.pdf">pdf</a>
{% endfor %}
