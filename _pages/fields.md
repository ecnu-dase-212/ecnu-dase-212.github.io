---
layout: page
title: 研究方向
permalink: /fields/
description: FIELDS # A collection of research fields.
nav: true
nav_order: 4
display_categories: [隐私保护机器学习, 金融科技, AIGC]
horizontal: true
---

<!-- pages/fields.md -->
<div class="fields">
{%- if site.enable_field_categories and page.display_categories %}
  <!-- Display categorized fields -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_fields = site.fields | where: "category", category -%}
  {%- assign sorted_fields = categorized_fields | sort: "importance" %}
  <!-- Generate cards for each field -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-1">
    {%- for field in sorted_fields -%}
      {% include fields_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for field in sorted_fields -%}
      {% include fields.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display fields without categories -->
  {%- assign sorted_fields = site.fields | sort: "importance" -%}
  <!-- Generate cards for each field -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for field in sorted_fields -%}
      {% include fields_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for field in sorted_fields -%}
      {% include fields.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
