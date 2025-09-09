---
layout: default
title: Research
permalink: /research/
---

{%- assign ongoing   = site.research | where: "completed", false | sort: "start" | reverse -%}
{%- assign completed = site.research | where: "completed", true  | sort: "end"   | reverse -%}

<section class="research-section">
  <h2 class="research-section-title">On-going Projects</h2>
  <div class="research-list">
    {%- for proj in ongoing -%}
      {%- assign s = proj.start | date: "%b %Y" -%}
      {%- assign e = proj.end   | date: "%b %Y" -%}
      {%- assign org    = proj.organization | default: proj.org -%}
      {%- assign sponsor = proj.agency      | default: proj.sponsor -%}

      <article class="research-card research-card--hero">
        <h3 class="research-title">{{ proj.title }}</h3>

        <div class="research-meta">
          {{ s }} – {{ e }}
          {%- if org or sponsor -%}
            &nbsp;•&nbsp;
            {%- if org -%}{{ org }}{%- endif -%}
            {%- if org and sponsor -%} · {%- endif -%}
            {%- if sponsor -%}{{ sponsor }}{%- endif -%}
          {%- endif -%}
        </div>

        {% if proj.image %}
        <div class="research-hero">
          <img src="{{ proj.image }}" alt="{{ proj.title }}">
        </div>
        {% endif %}

        {% if proj.description %}
        <div class="research-desc">
          {{ proj.description }}
        </div>
        {% endif %}
      </article>
    {%- endfor -%}
  </div>

  <h2 class="research-section-title">Completed Projects</h2>
  <div class="research-list">
    {%- for proj in completed -%}
      {%- assign s = proj.start | date: "%b %Y" -%}
      {%- assign e = proj.end   | date: "%b %Y" -%}
      {%- assign org    = proj.organization | default: proj.org -%}
      {%- assign sponsor = proj.agency      | default: proj.sponsor -%}

      <article class="research-card research-card--hero">
        <h3 class="research-title">{{ proj.title }}</h3>

        <div class="research-meta">
          {{ s }} – {{ e }}
          {%- if org or sponsor -%}
            &nbsp;•&nbsp;
            {%- if org -%}{{ org }}{%- endif -%}
            {%- if org and sponsor -%} · {%- endif -%}
            {%- if sponsor -%}{{ sponsor }}{%- endif -%}
          {%- endif -%}
        </div>

        {% if proj.image %}
        <div class="research-hero">
          <img src="{{ proj.image }}" alt="{{ proj.title }}">
        </div>
        {% endif %}

        {% if proj.description %}
        <div class="research-desc">
          {{ proj.description }}
        </div>
        {% endif %}
      </article>
    {%- endfor -%}
  </div>
</section>

