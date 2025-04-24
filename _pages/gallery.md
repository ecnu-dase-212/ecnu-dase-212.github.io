---
layout: page
title: 团队相册
permalink: /gallery/
description: GALLERY # A collection of gallery.
nav: true
nav_order: 5
display_categories: [学术会议, 聚会团建]
horizontal: true
---

<!-- pages/gallery.md -->
<div class="gallery">
{%- if site.enable_gallery_categories and page.display_categories %}
  <!-- Display categorized images -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_images = site.images | where: "category", category -%}
  {%- assign sorted_images = categorized_images | sort: "importance" %}
  <!-- Generate cards for each image -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-1">
    {%- for image in sorted_images -%}
      {% include gallery_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for image in sorted_images -%}
      {% include gallery.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display images without categories -->
  {%- assign sorted_images = site.images | sort: "importance" -%}
  <!-- Generate cards for each image -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for image in sorted_images -%}
      {% include gallery_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for image in sorted_images -%}
      {% include gallery.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
