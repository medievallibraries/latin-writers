---
layout: page
title: Writers
permalink: /writers/
---

<ul>
{% for writer in site.data.writers %}
  <li>
    <a href="{{ writer.id }}">
      {% if page.writer.type == "published" %}
        <span class="smallcaps">
      {% endif %}
        {{ writer.name }}
      {% if page.writer.type == "published" %}
        </span>
      {% endif %}
    </a>
  </li>
{% endfor %}
</ul>
