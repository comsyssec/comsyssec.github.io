---
layout: default
title: People
permalink: /people/
---

<h1>People</h1>

<ul>
  {% for person in site.people %}
    <li>
      <strong>{{ person.name }}</strong> - {{ person.position }}<br>
      {{ person.content | markdownify }}
    </li>
  {% endfor %}
</ul>
