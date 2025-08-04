---
layout: default
title: Teaching
permalink: /teaching/
---

<h1>Teaching</h1>

<ul>
  {% for course in site.teaching %}
    <li>
      <strong>{{ course.title }}</strong><br>
      {{ course.term }}<br>
      {{ course.description | markdownify }}
    </li>
  {% endfor %}
</ul>

