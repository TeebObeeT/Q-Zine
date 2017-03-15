---
layout: default
title: Catégories
---
{% assign categories_list = site.categories | sort %}

{% for category in categories_list %}
  <h2 class='category-header' id="{{ category[0] }}-ref">{{ category[0] }}</h2>
  <ul>
    {% assign pages_list = category[1] %}

    {% for node in pages_list %}
      {% if node.title != null %}
        {% if group == null or group == node.group %}
          {% if page.url == node.url %}
          <li class="active"><a href="{{ site.baseurl}}/{{ node.url }}" class="active">{{node.title}}</a></li>
          {% else %}
          <li><a href="{{ site.baseurl}}/{{node.url}}">{{node.title}}</a></li>
          {% endif %}
        {% endif %}
      {% endif %}
    {% endfor %}

    {% assign pages_list = nil %}
    {% assign group = nil %}
    {% assign categories_list = nil %}
  </ul>
{% endfor %}
