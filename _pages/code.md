---
title: "Code"
permalink: /code/
layout: single
excerpt: "A feed of my latest projects"
header:
  overlay_image: assets/images/code.jpg
  overlay_color: "#000"
  overlay_filter: "0.15"
  cta_label: "Github"
  cta_url: "https://github.com/byluong"
---
{% for project in site.portfolio %}
  <h2><a href="{{ project.url }}">{{ project.title }}</a></h2>
  {{project.content}}
{% endfor %}