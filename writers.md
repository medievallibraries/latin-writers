---
layout: page
title: Writers
permalink: /writers/
---

<ul>
{% for writer in site.writers %}
  <li>
    <a href="{{ writer.url | relative_url }}">
      {% if page.writer.type == "published" %}
        <span class="smallcaps">
      {% endif %}
        {{ writer.title }}
      {% if page.writer.type == "published" %}
        </span>
      {% endif %}
    </a>
  </li>
{% endfor %}
</ul>
