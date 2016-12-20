---
layout: archive
title: "Portfolio"
permalink: /portfolio/
author_profile: true
---

<div class="grid__wrapper">
  {% for post in site.portfolio %}
    {% include archive-single.md type="grid" %}
  {% endfor %}
</div>