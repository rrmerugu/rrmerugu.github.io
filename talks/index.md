---
layout: page
title: Talks
---

<div class="projects">
  {% for project in site.talks | reversed %}
  <div class="project post">
    <p class="title">
      <a href="{{ project.slides }}" target="_blank">
        {{ project.title }}
      </a>
      <small class="text-muted pull-right">{{ project.date | date_to_string }}</small>
    </p>
    <span class="project-tagline post-date">
        {{ project.tagline }}
    </span>
    <div class="color-999">
    {{ project.content }}
    </div>

  </div>
  {% endfor %}
</div>
