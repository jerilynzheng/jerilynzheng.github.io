---
layout: page
permalink: /play
title: Play
description:
nav: true
display_categories:
horizontal: false
---
<div class="play">
  {% if site.enable_play_categories and page.display_categories %}
  <!-- Display categorized play -->
    {% for category in page.display_categories %}
      <h2 class="category">{{category}}</h2>
      {% assign categorized_play = site.play | where: "category", category %}
      {% assign sorted_play = categorized_play | sort: "importance" %}
      <!-- Generate cards for each play -->
      {% if page.horizontal %}
        <div class="container">
          <div class="row row-cols-2">
          {% for play in sorted_play %}
            {% include play_horizontal.html %}
          {% endfor %}
          </div>
        </div>
      {% else %}
        <div class="container">
          <div class="row row-cols-2">
          {% for play in sorted_play %}
            {% include play.html %}
          {% endfor %}
        </div>
      {% endif %}
    {% endfor %}

  {% else %}
  <!-- Display play without categories -->
    {% assign sorted_play = site.play | sort: "importance" %}
    <!-- Generate cards for each play -->
    {% if page.horizontal %}
      <div class="container">
        <div class="row row-cols-2">
        {% for play in sorted_play %}
          {% include play_horizontal.html %}
        {% endfor %}
        </div>
      </div>
    {% else %}
      <div class="container">
        <div class="row row-cols-1 row-cols-xs-1 row-cols-sm-1 row-cols-md-2 row-cols-lg-2 row-cols-xl-2">
        {% for play in sorted_play %}
          {% include play.html %}
        {% endfor %}
        </div>
      </div>
    {% endif %}

  {% endif %}

</div>