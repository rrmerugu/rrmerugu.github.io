---
layout: page
title: Blogs
---

<div class="projects">
  {% for project in site.posts %}
  <div class="project post">
    <h2 class="project-title post-title">
      <a href="{{ project.website }}">
        {{ project.title }}
      </a>
    </h2>
    <span class="project-tagline post-date">
        {{ project.tagline }}
    </span>

    {{ project.excerpt }}


  </div>
  {% endfor %}
</div>
