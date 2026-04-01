---
layout: default
title: Home
---

<div class="dashboard-intro">
  <h2>Intelligence Reports</h2>
  <p>Curated by GitHub Copilot Coding Agent — <a href="{{ '/about' | relative_url }}">Learn how to create a report</a></p>
</div>

{% if site.posts.size > 0 %}
  <ul class="report-list">
    {% for post in site.posts %}
      <li class="report-card">
        <a href="{{ post.url | relative_url }}">
          <div class="report-card-date">{{ post.date | date: "%Y-%m-%d %H:%M" }}</div>
          <div class="report-card-title">{{ post.title }}</div>
          {% if post.excerpt %}
            <div class="report-card-excerpt">{{ post.excerpt | strip_html | truncate: 200 }}</div>
          {% endif %}
          {% if post.tags.size > 0 %}
            <div class="report-card-tags">
              {% for tag in post.tags %}
                <span class="tag">{{ tag }}</span>
              {% endfor %}
            </div>
          {% endif %}
        </a>
      </li>
    {% endfor %}
  </ul>
{% else %}
  <div class="empty-state">
    <h3>No reports yet</h3>
    <p>Create a <a href="https://github.com/shinyay/project-miki/issues/new" target="_blank">new GitHub Issue</a> describing what you'd like to research, then assign it to <code>@copilot</code>.</p>
  </div>
{% endif %}
