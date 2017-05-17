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
    </p>
    <span class="project-tagline post-date">
        {{ project.tagline }}
    </span>

    {{ project.content }}
    {{ project.date | date_to_string }}


  </div>
  {% endfor %}
</div>
