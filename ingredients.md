---
layout: default
title: Ingrédients
---
{% assign tags_list = site.tags | sort %}
{% for tag in tags_list %}
  <h2 class='tag-header' id="{{ tag[0] }}-ref">{{ tag[0] | capitalize }}</h2>
  <ul>
    {% assign pages_list = tag[1] %}

    {% for node in pages_list | sort %}
      {% if node.title != null %}
        {% if group == null or group == node.group %}
          {% if page.url == node.url %}
          <li class="active"><a href="{{ site.baseurl}}/{{node.url}}" class="active">{{node.title}}</a></li>
          {% else %}
          <li><a href="{{ site.baseurl}}/{{node.url}}">{{node.title}}</a></li>
          {% endif %}
        {% endif %}
      {% endif %}
    {% endfor %}

    {% assign pages_list = nil %}
    {% assign group = nil %}
    {% assign tags_list = nil %}
  </ul>
{% endfor %}
