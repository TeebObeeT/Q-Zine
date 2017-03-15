---
layout: default
title: Ingrédients
---

<div class='list-group'>
  <h1>Ingrédients</h1>
  {% assign tags_list = site.tags | sort %}

  {% if tags_list.first[0] == null %}
    {% for tag in tags_list %}
      <h2>
        <a href="#{{ tag }}-ref" class='list-group-item'>
          {{ tag }} <span class='badge'>{{ site.tags[tag].size }}</span>
        </a>
      </h2>
    {% endfor %}
  {% else %}
    {% for tag in tags_list %}
      <h2>
        <a href="#{{ tag[0] }}-ref" class='list-group-item'>
          {{ tag[0] }} <span class='badge'>{{ tag[1].size }}</span>
        </a>
      </h2>  
    {% endfor %}
  {% endif %}
</div>

{% for tag in tags_list %}
  <h1>Liste des recettes par ingrédient</h1>
  <h2 class='tag-header' id="{{ tag[0] }}-ref">{{ tag[0] }}</h2>
  <ul>
    {% assign pages_list = tag[1] %}

    {% for node in pages_list | sort %}
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
    {% assign tags_list = nil %}
  </ul>
{% endfor %}
