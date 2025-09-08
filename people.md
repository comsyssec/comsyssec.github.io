---
layout: default
title: People
permalink: /people/
---

{% assign order  = "professor|re|int|phd|ms|ui|alumni" | split: "|" %}
{% assign labels = "Professor|Researchers|M.S./Ph.D. Integrated Students|Ph.D. Students|M.S. Students|Undergraduate Interns|Alumni" | split: "|" %}

{% for idx in (0..order.size) %}
  {% assign code = order[idx] %}
  {% assign name = labels[idx] %}
  {% if code %}
    {% assign group = site.people | where: "role", code | sort_natural: "name" %}
    {% if group.size > 0 %}

<section class="people-section" id="{{ code }}">
  <h2 class="people-section-title">{{ name }}</h2>
  <div class="people-grid">
    {% for person in group %}
      <article class="person-card">
      {% if person.photo %}
        <img src="{{ person.photo }}" alt="{{ person.name }}" class="person-photo">
      {% endif %}

      <!-- 상단: 이름/직급 (사진 오른쪽에 한 줄 배치) -->
      <div class="person-head">
        <div class="person-name">{{ person.name }}</div>
        {% if person.position %}
          <div class="person-position">{{ person.position }}</div>
        {% endif %}
      

        {% if person.research %}
        <div class="person-tags">
          {% assign chips = person.research | split: "," %}
          {% for c in chips %}
            <span class="chip">{{ c | strip }}</span>
          {% endfor %}
        </div>
        {% endif %}
      </div>

      <!-- 하단: 설명(전체 너비) -->
      {% if person.content %}
        <div class="person-bio">{{ person.content | markdownify }}</div>
      {% endif %}

      <!-- 하단: 연락처(전체 너비) -->
      <div class="person-contacts">
        {% if person.email %}
          <a href="mailto:{{ person.email }}" class="icon-link">
            <img src="/assets/images/email.png" width="20">{{ person.email }}
          </a>
        {% endif %}
        {% if person.website %}
          <a href="{{ person.website }}" target="_blank" rel="noopener" class="icon-link">
            <img src="/assets/images/homepage.png" width="20">{{ person.website }}
          </a>
        {% endif %}
      </div>
    </article>

    {% endfor %}
  </div>
</section>

    {% endif %}
  {% endif %}
{% endfor %}

