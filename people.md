---
layout: default
title: People
permalink: /people/
---

<h1>People</h1>

<ul>
  {% for person in site.people | sort: "position" %}
    <li>
      <img src="{{ person.photo }}" alt="{{ person.name }}" style="max-width:120px;"><br>
      <strong>{{ person.name }}</strong> - {{ person.role }}<br>
      {{ person.position }}<br>
      Research: {{ person.research }}<br>
      Email: <a href="mailto:{{ person.email }}">{{ person.email }}</a><br>
      {% if person.website %}
        <a href="{{ person.website }}" target="_blank">Personal Website</a>
      {% endif %}
    </li>
  {% endfor %}
</ul>
