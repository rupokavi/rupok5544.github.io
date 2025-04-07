---
layout: page
title: Projects
permalink: /projects/
description: A growing collection of AI projects I worked on. Check them out!
nav: true
nav_order: 3
display_categories: [work, fun]
horizontal: false
published: true
---

<!-- pages/projects.md -->
<div class="projects">
<!-- Display projects without categories -->
  {%- assign sorted_projects = site.projects | sort: "importance" -%}
  <!-- Generate cards for each project -->
  <div class="grid">
    {%- for project in sorted_projects -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
</div>
