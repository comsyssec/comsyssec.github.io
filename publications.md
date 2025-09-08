---
layout: default
title: Publications
permalink: /publications/
---

<div class="pub-intro">
  <p>
    CSSLab aims to publish high-quality research papers in leading security, computer networks, and AI premium venues.<br>  
    ( <span class="badge-top">Top-tier</span>: internationally recognized premier conferences,  
      <span class="badge-ex">Excellent</span>: high-quality venues acknowledged as "excellent" by Korean Institute of Information Scientists and Engineers)
  </p>
</div>

{%- assign pubs = site.publications -%}
{%- assign type_order = "international|domestic|book|others" | split: "|" -%}

<div class="pubs">
{%- for type in type_order -%}
  {%- assign ptypes = pubs | where: "type", type -%}
  {%- if ptypes and ptypes.size > 0 -%}
    <h2 class="pub-type">
      {%- if type == "international" -%} International Conferences/Journals
      {%- elsif type == "domestic" -%} Domestic Conferences/Journals
      {%- elsif type == "book" -%} Book Chapters
      {%- else -%} Others
      {%- endif -%}
    </h2>

    {%- assign years = ptypes | map: "year" | uniq | sort | reverse -%}
    {%- for year in years -%}
      <h3 class="pub-year">{{ year }}</h3>

      {%- assign pyears = ptypes | where: "year", year -%}
      {%- assign sorted_year = pyears | sort: "month" | reverse -%}

      <ul class="pub-list">
        {%- for pub in sorted_year -%}
          <li class="pub-item">
            <!-- 순번 (연도 내) -->
            <div class="pub-num">#{{ forloop.index }}</div>

            <div class="pub-body">
              <div class="pub-title-line">
                {%- if pub.quality == "top" -%}
                  <span class="badge-top">Top-tier</span>
                {%- elsif pub.quality == "excellent" -%}
                  <span class="badge-ex">Excellent</span>
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
  {%- endif -%}
{%- endfor -%}
</div>

