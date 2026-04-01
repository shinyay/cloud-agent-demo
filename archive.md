---
layout: default
title: All Reports
permalink: /archive/
---

<main class="container" style="padding-top: 40px; padding-bottom: 60px;">
  <h2 class="section-title">📚 All Reports ({{ site.posts.size }})</h2>
  <p style="color: var(--color-text-secondary); margin-bottom: 24px;">
    Complete archive of all intelligence reports, newest first.
  </p>

  {% assign current_month = "" %}
  {% for post in site.posts %}
    {% assign post_month = post.date | date: "%Y年%m月" %}
    {% if post_month != current_month %}
      {% assign current_month = post_month %}
      <h3 style="font-size: 16px; font-weight: 700; color: var(--color-text-secondary); margin-top: 28px; margin-bottom: 12px; padding-bottom: 8px; border-bottom: 1px solid var(--color-border, #eee);">
        📅 {{ post.date | date: "%Y-%m" }}
      </h3>
    {% endif %}
    <div style="display: flex; align-items: baseline; gap: 12px; padding: 10px 0; border-bottom: 1px solid var(--color-border-light, #f3f3f3);">
      <span style="font-size: 13px; color: var(--color-text-secondary); min-width: 100px; font-variant-numeric: tabular-nums;">{{ post.date | date: "%m/%d %H:%M" }}</span>
      <div style="flex: 1;">
        <a href="{{ post.url | relative_url }}" style="font-weight: 600; font-size: 15px; color: var(--color-text); text-decoration: none;">{{ post.title }}</a>
        {% if post.tags.size > 0 %}
          <span style="margin-left: 8px;">
            {% for tag in post.tags limit:3 %}
              <span class="tag" style="font-size: 10px; padding: 1px 6px;">{{ tag }}</span>
            {% endfor %}
          </span>
        {% endif %}
        {% if post.excerpt %}
          <div style="font-size: 13px; color: var(--color-text-secondary); margin-top: 2px;">{{ post.excerpt | strip_html | truncate: 120 }}</div>
        {% endif %}
      </div>
    </div>
  {% endfor %}

  <div style="text-align: center; margin-top: 32px;">
    <a href="{{ '/' | relative_url }}" style="font-weight: 600; color: var(--color-primary, #0078D4);">← Back to Dashboard</a>
  </div>
</main>
