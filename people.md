---
layout: default
title: People
permalink: /people/
---

# People

{% assign order  = "professor|re|int|phd|ms|ui|alumni" | split: "|" %}
{% assign labels = "Professor|Researchers|M.S./Ph.D. Integrated Students|Ph.D. Students|M.S. Students|Undergraduate Interns|Alumni" | split: "|" %}

{% for idx in (0..order.size) %}
  {% assign code = order[idx] %}
  {% assign name = labels[idx] %}
  {% if code %}
    {% assign group = site.people | where: "role", code | sort_natural: "name" %}
    {% if group.size > 0 %}
<h2>{{ name }}</h2>
<div class="people-grid">
    {% for person in group %}
  <div class="person-card">
    {% if person.photo %}
  <img src="{{ person.photo }}" alt="{{ person.name }}" class="person-photo">
  {% endif %}
  <div class="person-meta">
  <div class="person-name">{{ person.name }}</div>
  {% if person.position %}<div class="person-position">{{ person.position }}</div>{% endif %}
  {% if person.research %}<div class="person-research">Research: {{ person.research }}</div>{% endif %}
  <div class="person-contacts">
  {% if person.email %}<a href="mailto:{{ person.email }}"><img src="/assets/images/email.png" width="20"> {{ person.email }}</a>{% endif %}
  {% if person.website %}{% if person.email %}<br>{% endif %}<a href="{{ person.website }}" target="_blank" rel="noopener"><img src="/assets/images/homepage.png" width="20"> {{ person.website }}</a>{% endif %}
  </div>
  {% if person.content %}{{ person.content }}{% endif %}
  </div>
  </div>
  {% endfor %}
</div>
  {% endif %}
  {% endif %}
{% endfor %}

