---
layout: single
title: Devoirs en ect2
permalink: /ect2/devoirs.html
sidebar:
  nav: "ect2"
---

{% assign dl = 1 %}
{% assign dc = 1 %}
{% assign ds = 1 %}

<ol>
{% for s in site.data.ect2.ect2_devoirs.devoirs %}
{% if s.type == "dl" %}
{% if s.bis %}
<li id="{{s.type}}_{{cpt}}">
<a href="./devoirs/ect2-dl{{cpt}}b_enonce.pdf">dl n°{{cpt}} bis</a> : {{s.title}}
</li>
{% else %}
{% if dl < 10 %}
{% assign cpt = "0" | append:dl %}
{% else %}
{% assign cpt = dl %}
{% endif %}
<li id="{{s.type}}_{{cpt}}">
<a href="./devoirs/ect2-dl{{cpt}}_enonce.pdf">dl n°{{cpt}}</a> : {{s.title}}
</li>
{% assign dl = dl | plus: 1 %}
{% endif %}

{% else %}
{% if s.type == "dc" %}
{% if dc < 10 %}
{% assign cpt = "0" | append:dc %}
{% else %}
{% assign cpt = dc %}
{% endif %}
<li>
<a href="./devoirs/ect2-dc{{cpt}}.pdf">dc n°{{cpt}}</a> : {{s.title}}
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
<a href="./devoirs/ect2-ds{{cpt}}_enonce.pdf">ds n°{{cpt}}</a> : {{s.title}}
</li>
{% assign ds = ds | plus: 1 %}
{% endif %}
{% endif %}
{% endif %}
{% endfor %}
</ol>
