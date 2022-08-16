---
layout: page
title: Works
permalink: /works/
---


<ul>

{% for work in site.works %}

  <li>
	<a href="{{ work.url | relative_url }}">
      {% for writer in site.writers %}
	  {% if work.writer == writer.id %}
	  {% if work.type == "spurious" %}‘{% endif %}{{ writer.title }}{% if work.type == "attributed" %} (attrib.){% endif %}{% if work.type == "spurious" %}’ (spurious){% endif %},
	  {% endif %}
      {% endfor %}
	  
	  {% unless work.title-description %}<cite>{% endunless %}
	  <span class="work-title"{% unless work.title-description %} lang="la"{% endunless %}>{{ work.title | markdownify | remove: '<p>' | remove: '</p>' }}</span>
	  {% unless work.title-description %}</cite>{% endunless %}
	</a>
  </li>
{% endfor %}
</ul>
