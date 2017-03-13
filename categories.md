---
layout: page
title: Catégories
---

<div class='list-group'>
  {% assign categories_list = site.categories | sort %}

  {% if categories_list.first[0] == null %}
    {% for category in categories_list %}
      <a href="/categories#{{ category }}-ref" class='list-group-item'>
        {{ category }} <span class='badge'>{{ site.categories[category].size }}</span>
      </a>
    {% endfor %}
  {% else %}
    {% for category in categories_list %}
      <a href="/categories#{{ category[0] }}-ref" class='list-group-item'>
        {{ category[0] }} <span class='badge'>{{ category[1].size }}</span>
      </a>
    {% endfor %}
  {% endif %}

  {% assign categories_list = nil %}
</div>


{% for category in site.categories %}
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
  </ul>
{% endfor %}
