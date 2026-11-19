---
layout: default
title: Publications
permalink: /publications/
---

<div class="pub-intro">
  <p>
    CSSLab aims to publish high-quality research papers in leading security, computer networks, and AI premium venues.<br>  
    ( <span class="pub-badge top">★ Top-tier</span>: internationally recognized premier conferences,  
      <span class="pub-badge ex">Excellent</span>: high-quality venues acknowledged as "excellent" by Korean Institute of Information Scientists and Engineers)
  </p>
</div>
{%- assign pubs = site.publications -%}
{%- assign type_order = "international|domestic|book|others" | split: "|" -%}

<div class="pub-tabs" role="tablist" aria-label="Publication type">
  <button class="pub-tab is-active" type="button"
          data-pub-tab="international" aria-selected="true">
    International Conferences/Journals
  </button>
  <button class="pub-tab" type="button"
          data-pub-tab="domestic" aria-selected="false">
    Domestic Conferences/Journals
  </button>
</div>

<div class="pubs">
  {%- for type in type_order -%}
    {%- assign ptypes = pubs | where: "type", type -%}
    {%- if ptypes.size > 0 -%}

      <section
        class="{% if type == 'international' or type == 'domestic' %}pub-panel{% else %}pub-extra{% endif %}"
        {% if type == "international" or type == "domestic" %}
          data-pub-panel="{{ type }}"
          {% if type == "domestic" %}hidden{% endif %}
        {% endif %}>

        {% if type == "book" %}
          <h2 class="pub-type">Book Chapters</h2>
        {% elsif type == "others" %}
          <h2 class="pub-type">Others</h2>
        {% endif %}

        {%- assign years = ptypes | map: "year" | uniq | sort | reverse -%}

        {%- for year in years -%}
          <h3 class="pub-year">{{ year }}</h3>

          {%- assign pyears = ptypes | where: "year", year -%}
          {%- assign sorted_year = pyears | sort: "month" | reverse -%}

          <ul class="pub-list">
            {%- for pub in sorted_year -%}
              <li class="pub-item">
                <div class="pub-num">#{{ forloop.index }}</div>

                <div class="pub-body">
                  <div class="pub-title-line">
                    {%- if pub.quality == "top" -%}
                      <span class="pub-badge top">★ Top-tier</span>
                    {%- elsif pub.quality == "excellent" -%}
                      <span class="pub-badge ex">Excellent</span>
                    {%- endif -%}

                    <span class="pub-title">{{ pub.title }}</span>

                    {%- if pub.paper -%}
                      <a class="pub-link" href="{{ pub.paper }}" target="_blank" rel="noopener">[Paper]</a>
                    {%- endif -%}
                    {%- if pub.proposal -%}
                      <a class="pub-link" href="{{ pub.proposal }}" target="_blank" rel="noopener">[Proposal]</a>
                    {%- endif -%}
                    {%- if pub.poster -%}
                      <a class="pub-link" href="{{ pub.poster }}" target="_blank" rel="noopener">[Poster]</a>
                    {%- endif -%}
                  </div>

                  <div class="pub-authors">{{ pub.authors }}</div>
                  <div class="pub-venue">
                    In {{ pub.venue }}{%- if pub.location -%}, {{ pub.location }}{%- endif -%}, {{ pub.year }}
                  </div>
                </div>
              </li>
            {%- endfor -%}
          </ul>
        {%- endfor -%}
      </section>
    {%- endif -%}
  {%- endfor -%}
</div>

<script>
document.addEventListener("DOMContentLoaded", function () {
  const tabs = document.querySelectorAll("[data-pub-tab]");
  const panels = document.querySelectorAll("[data-pub-panel]");

  tabs.forEach(tab => {
    tab.addEventListener("click", function () {
      const selected = this.dataset.pubTab;

      tabs.forEach(button => {
        const active = button === this;
        button.classList.toggle("is-active", active);
        button.setAttribute("aria-selected", active ? "true" : "false");
      });

      panels.forEach(panel => {
        panel.hidden = panel.dataset.pubPanel !== selected;
      });
    });
  });
});
</script>
