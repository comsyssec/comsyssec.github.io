---
layout: default
title: Publications
permalink: /publications/
---

<h1>Publications</h1>

{% assign pubs = site.publications %}

{% assign types = pubs | map: "type" | uniq | sort -%}
{% assign month_names = "January|February|March|April|May|June|July|August|September|October|November|December" | split: "|" -%}

{% for type in types %}
  <h2>
    {% if type == "international" %} International Conferences/Journals
    {% elsif type == "domestic" %} Domestic Conferences/Journals
    {% elsif type == "book" %} Book Chapters
    {% else %} Others
    {% endif %}
  </h2>

  {%- assign ptypes = pubs | where: "type", type -%}
  {%- assign years = ptypes | map: "year" | uniq | sort | reverse -%}

  {%- for year in years -%}
    <h3>{{ year }}</h3>

    {%- assign pyears = ptypes | where: "year", year -%}
    {%- assign sorted_year = pyears | sort: "month" | reverse -%}

    <ul class="pub-list">
      {%- for pub in sorted_year -%}
        {%- assign month_idx = pub.month | minus: 1 -%}
        {%- assign month_label = month_names[month_idx] -%}
        <li class="pub-item">
          <div class="pub-title">
            {%- if pub.top -%}
              <span class="badge-top">Top-tier</span>
            {%- endif -%}
            {{ pub.title }}
            {%- if pub.link -%}
            &nbsp;<a href="{{ pub.link }}" target="_blank" rel="noopener">[Paper]</a>
            {%- endif -%}
          </div>
          <div class="pub-authors">
            {{ pub.authors }}
          </div>
          <div class="pub-venue">
            In {{ pub.venue }}{%- if pub.location -%}, {{ pub.location }}{%- endif -%}, {{ month_label }} {{ pub.year }}
          </div>
        </li>
      {% endfor %}
    </ul>
  {% endfor %}
{% endfor %}
