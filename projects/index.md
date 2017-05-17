---
layout: page
title: Projects
---

<style>
h1{
  padding-bottom:20px;
  border-bottom:1px solid #eee;
  margin-bottom:15px;
}
</style>

<div class="projects">
  {% for project in site.projects reversed %}
  <div class="project post">
    <p class="title">
      <a href="{{ project.website }}" target="_blank">
        {{ project.title }}
      </a>
      <span class="pull-right color-999">    {{ project.date | date_to_string }}
      </span>
    </p>
    <span class="project-tagline post-date">
        {{ project.tagline }}
    </span>

    {{ project.content }}


  </div>
  {% endfor %}
</div>
