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

    <!-- Two-panel layout: main (today) + sidebar (older) -->
    <div class="dashboard-layout">

      <!-- Main area: today's reports -->
      <div class="dashboard-main">
        <h3 class="section-title">📋 Today's Reports</h3>
        <ul class="report-list" id="today-reports">
          {% for post in site.posts %}
            <li class="report-card" data-date="{{ post.date | date: '%Y-%m-%d' }}">
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
        <div id="no-today" class="empty-state" style="display: none;">
          <h3>No reports today yet</h3>
          <p><a href="https://github.com/shinyay/project-miki/issues/new?template=research-request.yml" target="_blank">Request a new report</a> to get started!</p>
        </div>
      </div>

      <!-- Sidebar: older reports (max 5) -->
      <aside class="dashboard-sidebar">
        <h3 class="section-title">📁 Recent Reports</h3>
        <ul class="sidebar-report-list" id="older-reports">
          {% for post in site.posts %}
            <li class="sidebar-report-item" data-date="{{ post.date | date: '%Y-%m-%d' }}" style="display: none;">
              <a href="{{ post.url | relative_url }}">
                <div class="sidebar-report-date">{{ post.date | date: "%m/%d %H:%M" }}</div>
                <div class="sidebar-report-title">{{ post.title }}</div>
                {% if post.excerpt %}
                  <div class="sidebar-report-excerpt">{{ post.excerpt | strip_html | truncate: 80 }}</div>
                {% endif %}
              </a>
            </li>
          {% endfor %}
        </ul>
        {% if site.posts.size > 5 %}
        <div style="text-align: center; padding-top: 12px; border-top: 1px solid var(--color-border, #eee); margin-top: 8px;">
          <a href="{{ '/archive' | relative_url }}" style="font-size: 14px; font-weight: 600; color: var(--color-primary, #0078D4);">View All Reports →</a>
        </div>
        {% endif %}
      </aside>

    </div>

  {% else %}
    <div class="empty-state">
      <h3>No reports yet</h3>
      <p>Create a <a href="https://github.com/shinyay/project-miki/issues/new?template=research-request.yml" target="_blank">new report request</a> and assign it to <code>@copilot</code>.</p>
    </div>
  {% endif %}
</main>

<script>
  // Split reports into "today" and "older" based on visitor's local date
  (function() {
    var today = new Date();
    var todayStr = today.getFullYear() + '-' +
      String(today.getMonth() + 1).padStart(2, '0') + '-' +
      String(today.getDate()).padStart(2, '0');

    var todayCards = document.querySelectorAll('#today-reports .report-card');
    var olderItems = document.querySelectorAll('#older-reports .sidebar-report-item');
    var hasTodayPosts = false;
    var olderCount = 0;

    todayCards.forEach(function(card) {
      if (card.dataset.date !== todayStr) {
        card.style.display = 'none';
      } else {
        hasTodayPosts = true;
      }
    });

    olderItems.forEach(function(item) {
      if (item.dataset.date !== todayStr) {
        olderCount++;
        if (olderCount <= 5) {
          item.style.display = 'block';
        }
      }
    });

    if (!hasTodayPosts) {
      document.getElementById('no-today').style.display = 'block';
    }
  })();
</script>
