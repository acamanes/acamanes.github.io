---
layout: single
title: Devoirs en d2
permalink: /d2/devoirs.html
sidebar:
  nav: "d2"
---

{% assign dl = 1 %}
{% assign dc = 1 %}
{% assign ds = 1 %}

<ol>
{% for s in site.data.d2.d2_devoirs.devoirs %}
{% if s.type == "dl" %}
{% if dl < 10 %}
{% assign cpt = "0" | append:dl %}
{% else %}
{% assign cpt = dl %}
{% endif %}
<li id="{{s.type}}_{{cpt}}">
<a href="./devoirs/d2-dl{{cpt}}_enonce.pdf">{{s.title}}</a>
</li>
{% assign dl = dl | plus: 1 %}

{% else %}
{% if s.type == "dc" %}
{% if dc < 10 %}
{% assign cpt = "0" | append:dc %}
{% else %}
{% assign cpt = dc %}
{% endif %}
<li>
<a href="./devoirs/d2-dc{{cpt}}.pdf">{{s.title}}</a>
</li>
{% assign dc = dc | plus: 1 %}

{% else %}
{% if s.type == "ds" %}
{% if ds < 10 %}
{% assign cpt = "0" | append:ds %}
{% else %}
{% assign cpt = ds %}
{% endif %}
<li>
<a href="./devoirs/d2-ds{{cpt}}_enonce.pdf">{{s.title}}</a>
</li>
{% assign ds = ds | plus: 1 %}
{% endif %}
{% endif %}
{% endif %}
{% endfor %}
</ol>
