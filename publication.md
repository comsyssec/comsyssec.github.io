---
layout: default
title: Publications
permalink: /publications/
---

<h1>Publications</h1>

<ul>
  {% assign pubs = site.publications | sort: 'year' | reverse %}
  {% for pub in pubs %}
    <li>
      <strong>{{ pub.title }}</strong><br>
      {{ pub.authors }}<br>
      <em>{{ pub.venue }}</em>, {{ pub.year }}<br>
      {{ pub.content | markdownify }}
    </li>
  {% endfor %}
</ul>
