---
layout: page
title: english
permalink: /english/
description: A growing collection of your cool english.
nav: true
nav_order: 2
display_categories: [language, learn]
horizontal: false
---

<!-- pages/english.md -->
<div class="english">
{%- if site.enable_english_categories and page.display_categories %}
  <!-- Display categorized english -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_english = site.english | where: "category", category -%}
  {%- assign sorted_english = categorized_english | sort: "importance" %}
  <!-- Generate cards for each english -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for english in sorted_english -%}
      {% include english_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for english in sorted_english -%}
      {% include english.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display english without categories -->
  {%- assign sorted_english = site.english | sort: "importance" -%}
  <!-- Generate cards for each english -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for english in sorted_english -%}
      {% include english_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for english in sorted_english -%}
      {% include english.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
