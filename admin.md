---
layout: default
title: Admin — Design Management
permalink: /admin/
---

<main class="container" style="padding-top: 40px; padding-bottom: 60px;">
  <h2 class="section-title">⚙️ Design Management</h2>
  <p style="color: var(--color-text-secondary); margin-bottom: 32px;">
    Create new designs or apply saved ones — all powered by Copilot Coding Agent.
    <br>
    新しいデザインの作成、または保存済みデザインの適用 — すべてCoding Agentが実行します。
  </p>

  <!-- Current Design -->
  <div style="background: var(--color-surface); border: 1px solid var(--color-border); border-radius: var(--radius, 12px); padding: 24px; margin-bottom: 24px;">
    <h3 style="margin-bottom: 16px;">📌 Current Design / 現在のデザイン</h3>
    {% for design in site.data.designs.designs %}
      {% if design.active %}
      <div style="display: flex; align-items: center; gap: 12px; flex-wrap: wrap;">
        <span style="font-size: 24px;">★</span>
        <div>
          <div style="font-weight: 700; font-size: 18px;">{{ design.name }}</div>
          <div style="color: var(--color-text-secondary); font-size: 14px;">{{ design.description }}</div>
          <div style="color: var(--color-text-secondary); font-size: 12px; margin-top: 4px;">Applied: {{ design.created }}</div>
        </div>
      </div>
      {% endif %}
    {% endfor %}
  </div>

  <!-- Create New Design -->
  <div style="background: var(--color-surface); border: 1px solid var(--color-border); border-radius: var(--radius, 12px); padding: 24px; margin-bottom: 24px;">
    <h3 style="margin-bottom: 8px;">✨ Create New Design / 新しいデザインを作成</h3>
    <p style="color: var(--color-text-secondary); font-size: 14px; margin-bottom: 16px;">
      Describe the design you want. The Coding Agent will rewrite the site's CSS and layouts.
    </p>

    <input type="text" id="design-name" placeholder="Design name (e.g., Dark Cyberpunk)"
      style="width: 100%; padding: 10px 14px; border: 1px solid var(--color-border, #ddd); border-radius: 8px; font-size: 15px; font-family: inherit; background: var(--color-bg, #f5f5f5); color: var(--color-text, #333); margin-bottom: 12px;">

    <textarea id="design-description" rows="5"
      placeholder="Describe the design in detail...&#10;&#10;Examples:&#10;• Apple-inspired minimalist: white space, subtle shadows, clean typography&#10;• Dark cyberpunk: neon accents on dark background, monospace elements&#10;• 和風デザイン: 紺色パレット、和紙テクスチャ、縦書き要素"
      style="width: 100%; padding: 12px 14px; border: 1px solid var(--color-border, #ddd); border-radius: 8px; font-size: 15px; font-family: inherit; background: var(--color-bg, #f5f5f5); color: var(--color-text, #333); resize: vertical; margin-bottom: 16px;"></textarea>

    <button onclick="submitNewDesign()"
      style="padding: 12px 28px; background: var(--color-primary, #0078D4); color: white; border: none; border-radius: 10px; font-weight: 700; cursor: pointer; font-size: 15px; font-family: inherit;">
      🎨 Create Design Issue
    </button>
  </div>

  <!-- Design Library -->
  <div style="background: var(--color-surface); border: 1px solid var(--color-border); border-radius: var(--radius, 12px); padding: 24px;">
    <h3 style="margin-bottom: 16px;">🎨 Design Library / デザインライブラリ</h3>

    {% for design in site.data.designs.designs %}
    <div style="display: flex; align-items: center; justify-content: space-between; padding: 14px 0; border-bottom: 1px solid var(--color-border, #eee); flex-wrap: wrap; gap: 12px;">
      <div style="flex: 1; min-width: 200px;">
        <div style="font-weight: 600; font-size: 16px;">
          {% if design.active %}★ {% endif %}{{ design.name }}
          {% if design.active %}
            <span style="background: var(--color-primary, #0078D4); color: white; padding: 2px 8px; border-radius: 10px; font-size: 11px; font-weight: 600; margin-left: 8px;">ACTIVE</span>
          {% endif %}
        </div>
        <div style="color: var(--color-text-secondary); font-size: 13px; margin-top: 2px;">{{ design.description | truncate: 100 }}</div>
        <div style="color: var(--color-text-secondary); font-size: 11px; margin-top: 2px;">Created: {{ design.created }}</div>
      </div>
      {% unless design.active %}
      <button onclick="applyDesign('{{ design.name }}', '{{ design.slug }}')"
        style="padding: 8px 20px; background: var(--color-surface-hover, #f0f0f0); border: 1px solid var(--color-border, #ddd); border-radius: 8px; font-weight: 600; cursor: pointer; font-size: 13px; font-family: inherit; color: var(--color-text, #333); transition: all 0.3s;">
        Apply / 適用
      </button>
      {% endunless %}
    </div>
    {% endfor %}

    {% if site.data.designs.designs.size == 0 %}
    <p style="color: var(--color-text-secondary); text-align: center; padding: 20px;">No designs saved yet.</p>
    {% endif %}
  </div>
</main>

<script>
  function submitNewDesign() {
    const name = document.getElementById('design-name').value.trim();
    const description = document.getElementById('design-description').value.trim();

    if (!name || !description) {
      alert('Please enter both a name and description / 名前と説明を入力してください');
      return;
    }

    const body = [
      '## Design Request',
      '',
      '**Design Name:** ' + name,
      '**Description:**',
      description,
      '',
      '---',
      '',
      '### Instructions for Design Specialist Agent',
      '1. Create a complete new design based on the description above',
      '2. Rewrite `assets/css/style.css` with the new design',
      '3. Update `_layouts/default.html` and `_layouts/post.html` if needed',
      '4. Update `index.md` if dashboard layout changes are needed',
      '5. Save the new CSS as `assets/css/themes/' + name.toLowerCase().replace(/[^a-z0-9]+/g, '-').replace(/-+$/, '') + '.css`',
      '6. Update `_data/designs.yml` — add new entry with `active: true`, set all others to `active: false`',
    ].join('\n');

    const title = encodeURIComponent('[Design] ' + name);
    const encodedBody = encodeURIComponent(body);
    const url = 'https://github.com/shinyay/project-miki/issues/new?title=' + title + '&body=' + encodedBody + '&labels=design';

    window.open(url, '_blank');
  }

  function applyDesign(name, slug) {
    const body = [
      '## Apply Saved Design',
      '',
      '**Design:** ' + name,
      '**Theme file:** `assets/css/themes/' + slug + '.css`',
      '',
      '---',
      '',
      '### Instructions for Design Specialist Agent',
      '1. Read the saved CSS from `assets/css/themes/' + slug + '.css`',
      '2. Replace `assets/css/style.css` with the saved CSS content',
      '3. Update `_data/designs.yml` — set `' + name + '` to `active: true`, all others to `active: false`',
      '4. Do NOT modify any other files',
    ].join('\n');

    const title = encodeURIComponent('[Design] Apply: ' + name);
    const encodedBody = encodeURIComponent(body);
    const url = 'https://github.com/shinyay/project-miki/issues/new?title=' + title + '&body=' + encodedBody + '&labels=design';

    window.open(url, '_blank');
  }
</script>
