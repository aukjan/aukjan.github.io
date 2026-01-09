---
layout: page
title: Thought Leadership
subtitle: Articles on Technology, Product Strategy, and Leadership
---

<div class="post-list">
  {% if site.posts.size == 0 %}
    <div style="text-align: center; padding: var(--space-3xl) 0;">
      <p class="lead">Coming soon.</p>
      <p>
        This section will feature articles on tech trends, product innovation,
        scaling teams, and strategic leadership.
      </p>
    </div>
  {% else %}
    <div class="grid grid-cols-2">
      {% for post in site.posts %}
        <article class="card">
          <h3 class="card-title">
            <a href="{{ post.url }}" style="text-decoration: none; color: inherit;">
              {{ post.title }}
            </a>
          </h3>
          <div class="post-meta">
            <time datetime="{{ post.date | date_to_xmlschema }}">
              {{ post.date | date: "%B %d, %Y" }}
            </time>
          </div>
          {% if post.excerpt %}
            <p class="card-content">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
          {% endif %}
          <a href="{{ post.url }}" class="btn btn-secondary" style="margin-top: var(--space-sm);">
            Read More →
          </a>
        </article>
      {% endfor %}
    </div>
  {% endif %}
</div>
