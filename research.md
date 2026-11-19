---
layout: default
title: Research
permalink: /research/
---

{%- assign ongoing   = site.research | where: "completed", false | sort: "start" | reverse -%}
{%- assign completed = site.research | where: "completed", true  | sort: "end"   | reverse -%}

<section class="research-section">

  <div class="research-tabs" role="tablist" aria-label="Research projects">
    <button class="research-tab is-active" type="button"
            data-research-tab="ongoing" aria-selected="true">
      On-going Projects
    </button>
    <button class="research-tab" type="button"
            data-research-tab="completed" aria-selected="false">
      Completed Projects
    </button>
  </div>

  <div class="research-panel" data-research-panel="ongoing">
    <div class="research-list">
      {%- for proj in ongoing -%}
        {%- assign s = proj.start | date: "%b %Y" -%}
        {%- assign e = proj.end | date: "%b %Y" -%}
        {%- assign org = proj.organization | default: proj.org -%}
        {%- assign sponsor = proj.agency | default: proj.sponsor -%}

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
          <div class="research-desc">{{ proj.description }}</div>
          {% endif %}
        </article>
      {%- endfor -%}
    </div>
  </div>

  <div class="research-panel" data-research-panel="completed" hidden>
    <div class="research-list">
      {%- for proj in completed -%}
        {%- assign s = proj.start | date: "%b %Y" -%}
        {%- assign e = proj.end | date: "%b %Y" -%}
        {%- assign org = proj.organization | default: proj.org -%}
        {%- assign sponsor = proj.agency | default: proj.sponsor -%}

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
          <div class="research-desc">{{ proj.description }}</div>
          {% endif %}
        </article>
      {%- endfor -%}
    </div>
  </div>

</section>

<script>
document.addEventListener("DOMContentLoaded", function () {
  const tabs = document.querySelectorAll("[data-research-tab]");
  const panels = document.querySelectorAll("[data-research-panel]");

  tabs.forEach(tab => {
    tab.addEventListener("click", function () {
      const selected = this.dataset.researchTab;

      tabs.forEach(button => {
        const active = button === this;
        button.classList.toggle("is-active", active);
        button.setAttribute("aria-selected", active ? "true" : "false");
      });

      panels.forEach(panel => {
        panel.hidden = panel.dataset.researchPanel !== selected;
      });
    });
  });
});
</script>
