---
layout: page
title: Works
permalink: /works/
---


<ul>

{% for work in site.works %}

  <li>
  <a href="{{ work.url | relative_url }}">
    {% assign workWriter = site.writers | where_exp: 'writer', 'writer.identifier == work.writer' %}
    {% for writer in workWriter %}
      {% if work.subtype == "spurious" %}‘{% endif %}{{ writer.title }}{% if work.subtype == "attributed" %} (attrib.){% endif %}{% if work.subtype == "spurious" %}’ (spurious){% endif %},
    {% endfor %}
    
    {% unless work.title-description %}<cite>{% endunless %}
    <span class="work-title"{% unless work.title-description %} lang="la"{% endunless %}>{{ work.title | markdownify | remove: '<p>' | remove: '</p>' }}</span>
    {% unless work.title-description %}</cite>{% endunless %}
  </a>
  </li>
{% endfor %}
</ul>
