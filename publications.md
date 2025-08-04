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
      {% if pub.top %}
        <span style="background: gold; color: black; padding: 2px 4px; border-radius: 4px; font-size: 0.8em;">Top-tier</span>
      {% endif %}
      <strong>{{ pub.title }}</strong><br>
      {{ pub.authors }}<br>
      <em>{{ pub.venue }}</em>, {{ pub.year }}<br>
    </li>
  {% endfor %}
</ul>
