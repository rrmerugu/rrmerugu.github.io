---
layout: page
title: Projects
---

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
