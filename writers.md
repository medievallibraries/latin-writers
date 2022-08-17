---
layout: page
title: Writers
permalink: /writers/
---

<ul>
{% for writer in site.writers %}
  <li>
    <a href="{{ writer.url | relative_url }}">
      {% if writer.subtype == "published" %}
        <span class="smallcaps">
      {% endif %}
        {{ writer.title }}
      {% if writer.subtype == "published" %}
        </span>
      {% endif %}
    </a>
  </li>
{% endfor %}
</ul>
