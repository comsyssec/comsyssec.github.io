{% assign role_order = "professor|phd|ms|ug|alumni" | split: "|" %}
{% assign role_labels = "Professor|Ph.D. Students|M.S. Students|Undergraduate Interns|Alumni" | split: "|" %}

{% for idx in (0..role_order.size) %}
  {% assign role_code = role_order[idx] %}
  {% assign role_name = role_labels[idx] %}
  {% if role_code %}
    {% assign group = site.people | where: "role", role_code | sort_natural: "name" %}
    {% if group.size > 0 %}
      <h2>{{ role_name }}</h2>
      <div class="people-grid">
        {% for person in group %}
          <div class="person-card">
            {% if person.photo %}
              <img src="{{ person.photo }}" alt="{{ person.name }}" class="person-photo">
            {% endif %}
            <div class="person-meta">
              <div class="person-name">{{ person.name }}</div>
              {% if person.position %}<div class="person-position">{{ person.position }}</div>{% endif %}
              {% if person.research %}<div class="person-research">Research:{{ person.research }}</div>{% endif %}
              <div class="person-contacts">
                {% if person.email %}E-mail:<a href="mailto:{% raw %}{{{% endraw %} person.email {% raw %}}}{% endraw %}">{{ person.email }}</a>{% endif %}
                {% if person.website %}Webpage:<a href="{{ person.website }}" target="_blank" rel="noopener">{{ person.website }}</a>{% endif %}
              </div>
              {% if person.content %}{{ person.content | markdownify }}{% endif %}
            </div>
          </div>
        {% endfor %}
      </div>
    {% endif %}
  {% endif %}
{% endfor %}

