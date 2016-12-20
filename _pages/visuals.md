---
layout: archive
title: "Visuals"
permalink: /visuals/
author_profile: false
---
<div class="grid__wrapper">
  {% for post in site.visuals %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>