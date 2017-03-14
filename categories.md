---
layout: default
title: Catégories
---

<div class='list-group'>
  {% assign categories_list = site.categories | sort %}

  {% if categories_list.first[0] == null %}
    <ul>
      {% for category in categories_list %}
        <li>
          <a href="#{{ category }}-ref" class='list-group-item'>
            {{ category }} <span class='badge'>{{ site.categories[category].size }}</span>
          </a>
        </li>
      {% endfor %}
    </ul>
  {% else %}
    <ul>
      {% for category in categories_list %}
        <li>
          <a href="#{{ category[0] }}-ref" class='list-group-item'>
            {{ category[0] }} <span class='badge'>{{ category[1].size }}</span>
          </a>
        </li>
      {% endfor %}
    </ul>
  {% endif %}
</div>


{% for category in categories_list %}
  <h2 class='category-header' id="{{ category[0] }}-ref">{{ category[0] }}</h2>
  <ul>
    {% assign pages_list = category[1] %}

    {% for node in pages_list %}
      {% if node.title != null %}
        {% if group == null or group == node.group %}
          {% if page.url == node.url %}
          <li class="active"><a href="{{node.url}}" class="active">{{node.title}}</a></li>
          {% else %}
          <li><a href="{{node.url}}">{{node.title}}</a></li>
          {% endif %}
        {% endif %}
      {% endif %}
    {% endfor %}

    {% assign pages_list = nil %}
    {% assign group = nil %}
    {% assign categories_list = nil %}
  </ul>
{% endfor %}
