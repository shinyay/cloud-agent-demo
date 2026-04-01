---
layout: default
title: Admin — Manage Sources
permalink: /admin/
---

<main class="container" style="padding-top: 40px;">
  <h2 class="section-title">⚙️ Admin — Information Sources</h2>
  <p style="color: var(--color-text-secondary); margin-bottom: 24px;">
    Manage the domains the Coding Agent can access. Changes are submitted as a GitHub Issue for processing.
    <br>
    Coding Agentがアクセスできるドメインを管理します。変更はGitHub Issueとして送信されます。
  </p>

  <div style="background: var(--color-surface); border: 1px solid var(--color-border); border-radius: var(--radius, 12px); padding: 24px; margin-bottom: 24px;">
    <h3 style="margin-bottom: 16px;">📂 Current Sources — Microsoft</h3>
    <div id="microsoft-sources">
      {% for source in site.data.sources.microsoft %}
      <label style="display: flex; align-items: center; gap: 10px; padding: 8px 0; border-bottom: 1px solid var(--color-border, #eee); cursor: pointer;">
        <input type="checkbox" class="source-checkbox" data-domain="{{ source.domain }}" data-label="{{ source.label }}" checked>
        <span style="font-weight: 600; min-width: 240px;">{{ source.domain }}</span>
        <span style="color: var(--color-text-secondary, #666); font-size: 14px;">{{ source.label }}</span>
      </label>
      {% endfor %}
    </div>
  </div>

  <div style="background: var(--color-surface); border: 1px solid var(--color-border); border-radius: var(--radius, 12px); padding: 24px; margin-bottom: 24px;">
    <h3 style="margin-bottom: 16px;">🐙 Current Sources — GitHub</h3>
    <div id="github-sources">
      {% for source in site.data.sources.github %}
      <label style="display: flex; align-items: center; gap: 10px; padding: 8px 0; border-bottom: 1px solid var(--color-border, #eee); cursor: pointer;">
        <input type="checkbox" class="source-checkbox" data-domain="{{ source.domain }}" data-label="{{ source.label }}" checked>
        <span style="font-weight: 600; min-width: 240px;">{{ source.domain }}</span>
        <span style="color: var(--color-text-secondary, #666); font-size: 14px;">{{ source.label }}</span>
      </label>
      {% endfor %}
    </div>
  </div>

  <div style="background: var(--color-surface); border: 1px solid var(--color-border); border-radius: var(--radius, 12px); padding: 24px; margin-bottom: 24px;">
    <h3 style="margin-bottom: 16px;">➕ Add New Domain</h3>
    <div style="display: flex; gap: 12px; flex-wrap: wrap;">
      <input type="text" id="new-domain" placeholder="example.com" style="flex: 1; min-width: 200px; padding: 10px 14px; border: 1px solid var(--color-border, #ddd); border-radius: 8px; font-size: 15px; font-family: inherit; background: var(--color-bg, #f5f5f5); color: var(--color-text, #333);">
      <input type="text" id="new-label" placeholder="Description (optional)" style="flex: 1; min-width: 200px; padding: 10px 14px; border: 1px solid var(--color-border, #ddd); border-radius: 8px; font-size: 15px; font-family: inherit; background: var(--color-bg, #f5f5f5); color: var(--color-text, #333);">
      <button onclick="addDomain()" style="padding: 10px 20px; background: var(--color-primary, #0078D4); color: white; border: none; border-radius: 8px; font-weight: 600; cursor: pointer; font-size: 15px; font-family: inherit;">Add</button>
    </div>
    <div id="new-domains-list" style="margin-top: 12px;"></div>
  </div>

  <div style="display: flex; gap: 12px; justify-content: flex-end;">
    <button onclick="submitChanges()" id="submit-btn" style="padding: 12px 28px; background: var(--color-primary, #0078D4); color: white; border: none; border-radius: 10px; font-weight: 700; cursor: pointer; font-size: 16px; font-family: inherit; transition: all 0.3s;">
      📝 Submit Changes as Issue
    </button>
  </div>
</main>

<script>
  const newDomains = [];

  function addDomain() {
    const domainInput = document.getElementById('new-domain');
    const labelInput = document.getElementById('new-label');
    const domain = domainInput.value.trim();
    const label = labelInput.value.trim() || 'Custom source';

    if (!domain) return;
    if (newDomains.find(d => d.domain === domain)) return;

    newDomains.push({ domain, label });
    domainInput.value = '';
    labelInput.value = '';
    renderNewDomains();
  }

  function removeDomain(index) {
    newDomains.splice(index, 1);
    renderNewDomains();
  }

  function renderNewDomains() {
    const list = document.getElementById('new-domains-list');
    if (newDomains.length === 0) {
      list.innerHTML = '';
      return;
    }
    list.innerHTML = newDomains.map((d, i) =>
      '<div style="display: flex; align-items: center; gap: 10px; padding: 6px 0;">' +
        '<span style="color: #28A745;">✅</span> ' +
        '<span style="font-weight: 600;">' + d.domain + '</span> ' +
        '<span style="color: var(--color-text-secondary, #666); font-size: 14px;">' + d.label + '</span> ' +
        '<button onclick="removeDomain(' + i + ')" style="background: none; border: none; color: #EF4444; cursor: pointer; font-size: 16px;">✕</button>' +
      '</div>'
    ).join('');
  }

  function submitChanges() {
    // Collect unchecked (to remove)
    const removals = [];
    document.querySelectorAll('.source-checkbox').forEach(cb => {
      if (!cb.checked) {
        removals.push(cb.dataset.domain + ' (' + cb.dataset.label + ')');
      }
    });

    // Build issue body
    let body = '## Source Changes Request\\n\\n';

    if (removals.length > 0) {
      body += '### ❌ Domains to Remove\\n';
      removals.forEach(r => { body += '- ' + r + '\\n'; });
      body += '\\n';
    }

    if (newDomains.length > 0) {
      body += '### ✅ Domains to Add\\n';
      newDomains.forEach(d => { body += '- `' + d.domain + '` — ' + d.label + '\\n'; });
      body += '\\n';
    }

    if (removals.length === 0 && newDomains.length === 0) {
      alert('No changes to submit / 変更がありません');
      return;
    }

    body += '### 📋 Action Required\\n';
    body += '1. Update `_data/sources.yml` in the repo\\n';
    body += '2. Run: `gh variable set COPILOT_AGENT_FIREWALL_ALLOW_LIST_ADDITIONS --body "NEW_COMMA_SEPARATED_LIST"`\\n';
    body += '3. Update the issue form dropdown if needed\\n';

    const title = encodeURIComponent('[Admin] Update Information Sources');
    const encodedBody = encodeURIComponent(body.replace(/\\n/g, '\n'));
    const labels = encodeURIComponent('admin');
    const url = 'https://github.com/shinyay/project-miki/issues/new?title=' + title + '&body=' + encodedBody + '&labels=' + labels;

    window.open(url, '_blank');
  }
</script>
