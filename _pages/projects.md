---
layout: page
title: projects
permalink: /projects/
description: Research projects on optimization, control, and variational analysis, plus undergraduate research ideas for AMS 487 and prospective students at SUNY Korea.
nav: true
nav_order: 3
display_categories: [research, undergraduate]
horizontal: false
---

<div class="card mb-4">
  <div class="card-body">
    <h2 class="h4 mt-0">Preparing for undergraduate research</h2>
    <p class="mb-3">
      Before choosing a project, review the recommended mathematics, computing,
      optimization, and research-practice pathway for work in optimal control,
      nonsmooth dynamics, robotics, traffic and crowd models, or safe reinforcement
      learning.
    </p>
    <a class="btn btn-sm btn-outline-primary" href="/undergraduate-research/">
      View the undergraduate research learning path
    </a>
  </div>
</div>

<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
