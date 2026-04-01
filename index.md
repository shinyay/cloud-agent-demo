---
layout: default
title: Home
---

<section class="hero">
  <div class="container">
    <h2 class="hero-title">🌸 Intelligence Dashboard</h2>
    <p class="hero-subtitle">AI-curated reports from Microsoft and GitHub sources — powered by GitHub Copilot Coding Agent</p>
    <div class="hero-stats">
      <div class="hero-stat">
        <div class="hero-stat-number">{{ site.posts.size }}</div>
        <div class="hero-stat-label">Reports</div>
      </div>
      <div class="hero-stat">
        <div class="hero-stat-number">13</div>
        <div class="hero-stat-label">Sources</div>
      </div>
      <div class="hero-stat">
        <div class="hero-stat-number">7</div>
        <div class="hero-stat-label">Tone Styles</div>
      </div>
    </div>
    <a href="https://github.com/shinyay/project-miki/issues/new?template=research-request.yml" target="_blank" class="hero-cta">✨ Request New Report</a>
  </div>
</section>

<main class="container">
  {% if site.posts.size > 0 %}
    <h3 class="section-title">📋 Recent Reports</h3>
    <ul class="report-list">
      {% for post in site.posts %}
        <li class="report-card">
          <a href="{{ post.url | relative_url }}">
            <div class="report-card-date">📅 {{ post.date | date: "%Y-%m-%d %H:%M" }}</div>
            <div class="report-card-title">{{ post.title }}</div>
            {% if post.excerpt %}
              <div class="report-card-excerpt">{{ post.excerpt | strip_html | truncate: 160 }}</div>
            {% endif %}
            <div class="report-card-footer">
              <div class="report-card-tags">
                {% if post.tone %}
                  <span class="tag tone-tag">🎨 {{ post.tone }}</span>
                {% endif %}
                {% for tag in post.tags %}
                  <span class="tag">{{ tag }}</span>
                {% endfor %}
              </div>
            </div>
          </a>
        </li>
      {% endfor %}
    </ul>
  {% else %}
    <div class="empty-state">
      <h3>No reports yet</h3>
      <p>Create a <a href="https://github.com/shinyay/project-miki/issues/new?template=research-request.yml" target="_blank">new report request</a> and assign it to <code>@copilot</code>.</p>
    </div>
  {% endif %}
</main>
