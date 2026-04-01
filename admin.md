---
layout: default
title: Admin
permalink: /admin/
---

<main class="container" style="padding-top: 40px; padding-bottom: 60px;">
  <h2 class="section-title">⚙️ Admin</h2>

  <!-- Tab Navigation -->
  <div style="display: flex; gap: 4px; margin-bottom: 24px; border-bottom: 2px solid var(--color-border, #eee);">
    <button class="admin-tab" onclick="switchTab('design')" id="tab-design"
      style="padding: 10px 20px; border: none; background: none; font-size: 15px; font-weight: 600; cursor: pointer; font-family: inherit; color: var(--color-primary, #0078D4); border-bottom: 2px solid var(--color-primary, #0078D4); margin-bottom: -2px;">
      🎨 Design
    </button>
    <button class="admin-tab" onclick="switchTab('agents')" id="tab-agents"
      style="padding: 10px 20px; border: none; background: none; font-size: 15px; font-weight: 600; cursor: pointer; font-family: inherit; color: var(--color-text-secondary, #666); border-bottom: 2px solid transparent; margin-bottom: -2px;">
      🤖 Custom Agents
    </button>
  </div>

  <!-- ==================== DESIGN TAB ==================== -->
  <div id="panel-design">
    <div style="background: var(--color-surface); border: 1px solid var(--color-border); border-radius: var(--radius, 12px); padding: 24px; margin-bottom: 24px;">
      <h3 style="margin-bottom: 16px;">📌 Current Design</h3>
      {% for design in site.data.designs.designs %}{% if design.active %}
      <div style="display: flex; align-items: center; gap: 12px; flex-wrap: wrap;">
        <span style="font-size: 24px;">★</span>
        <div>
          <div style="font-weight: 700; font-size: 18px;">{{ design.name }}</div>
          <div style="color: var(--color-text-secondary); font-size: 14px;">{{ design.description }}</div>
          <div style="color: var(--color-text-secondary); font-size: 12px; margin-top: 4px;">Applied: {{ design.created }}</div>
        </div>
      </div>
      {% endif %}{% endfor %}
    </div>

    <div style="background: var(--color-surface); border: 1px solid var(--color-border); border-radius: var(--radius, 12px); padding: 24px; margin-bottom: 24px;">
      <h3 style="margin-bottom: 8px;">✨ Create New Design</h3>
      <p style="color: var(--color-text-secondary); font-size: 14px; margin-bottom: 16px;">Describe the design. Coding Agent will rewrite CSS and layouts.</p>
      <input type="text" id="design-name" placeholder="Design name (e.g., Dark Cyberpunk)" style="width: 100%; padding: 10px 14px; border: 1px solid var(--color-border, #ddd); border-radius: 8px; font-size: 15px; font-family: inherit; background: var(--color-bg, #f5f5f5); color: var(--color-text, #333); margin-bottom: 12px;">
      <textarea id="design-description" rows="4" placeholder="Describe the design in detail..." style="width: 100%; padding: 12px 14px; border: 1px solid var(--color-border, #ddd); border-radius: 8px; font-size: 15px; font-family: inherit; background: var(--color-bg, #f5f5f5); color: var(--color-text, #333); resize: vertical; margin-bottom: 16px;"></textarea>
      <button onclick="submitNewDesign()" style="padding: 12px 28px; background: var(--color-primary, #0078D4); color: white; border: none; border-radius: 10px; font-weight: 700; cursor: pointer; font-size: 15px; font-family: inherit;">🎨 Create Design Issue</button>
    </div>

    <div style="background: var(--color-surface); border: 1px solid var(--color-border); border-radius: var(--radius, 12px); padding: 24px;">
      <h3 style="margin-bottom: 16px;">🎨 Design Library</h3>
      {% for design in site.data.designs.designs %}
      <div style="display: flex; align-items: center; justify-content: space-between; padding: 14px 0; border-bottom: 1px solid var(--color-border, #eee); flex-wrap: wrap; gap: 12px;">
        <div style="flex: 1; min-width: 200px;">
          <div style="font-weight: 600;">{% if design.active %}★ {% endif %}{{ design.name }}{% if design.active %}<span style="background: var(--color-primary, #0078D4); color: white; padding: 2px 8px; border-radius: 10px; font-size: 11px; margin-left: 8px;">ACTIVE</span>{% endif %}</div>
          <div style="color: var(--color-text-secondary); font-size: 13px;">{{ design.description | truncate: 100 }}</div>
        </div>
        {% unless design.active %}<button onclick="applyDesign('{{ design.name }}', '{{ design.slug }}')" style="padding: 8px 20px; background: var(--color-surface-hover, #f0f0f0); border: 1px solid var(--color-border, #ddd); border-radius: 8px; font-weight: 600; cursor: pointer; font-size: 13px; font-family: inherit; color: var(--color-text, #333);">Apply</button>{% endunless %}
      </div>
      {% endfor %}
    </div>
  </div>

  <!-- ==================== AGENTS TAB ==================== -->
  <div id="panel-agents" style="display: none;">
    <div style="background: var(--color-surface); border: 1px solid var(--color-border); border-radius: var(--radius, 12px); padding: 24px; margin-bottom: 24px;">
      <h3 style="margin-bottom: 8px;">🛠️ Create New Custom Agent</h3>
      <p style="color: var(--color-text-secondary); font-size: 14px; margin-bottom: 16px;">Describe the agent you need. The Agent Creator will build it.<br>必要なエージェントを説明してください。Agent Creatorが作成します。</p>
      <input type="text" id="agent-name" placeholder="Agent name (e.g., Meeting Minutes Writer)" style="width: 100%; padding: 10px 14px; border: 1px solid var(--color-border, #ddd); border-radius: 8px; font-size: 15px; font-family: inherit; background: var(--color-bg, #f5f5f5); color: var(--color-text, #333); margin-bottom: 12px;">
      <textarea id="agent-description" rows="4" placeholder="Describe the agent's role and capabilities...&#10;&#10;Examples:&#10;• Meeting minutes writer&#10;• Email draft composer&#10;• 議事録作成エージェント" style="width: 100%; padding: 12px 14px; border: 1px solid var(--color-border, #ddd); border-radius: 8px; font-size: 15px; font-family: inherit; background: var(--color-bg, #f5f5f5); color: var(--color-text, #333); resize: vertical; margin-bottom: 16px;"></textarea>
      <button onclick="submitNewAgent()" style="padding: 12px 28px; background: var(--color-primary, #0078D4); color: white; border: none; border-radius: 10px; font-weight: 700; cursor: pointer; font-size: 15px; font-family: inherit;">🛠️ Create Agent Issue</button>
    </div>

    <div style="background: var(--color-surface); border: 1px solid var(--color-border); border-radius: var(--radius, 12px); padding: 24px;">
      <h3 style="margin-bottom: 16px;">🤖 Registered Agents ({{ site.data.agents.agents.size }})</h3>
      {% for agent in site.data.agents.agents %}
      <div style="display: flex; align-items: center; justify-content: space-between; padding: 14px 0; border-bottom: 1px solid var(--color-border, #eee); flex-wrap: wrap; gap: 12px;">
        <div style="flex: 1; min-width: 200px;">
          <div style="font-weight: 600; font-size: 16px;">{{ agent.icon }} {{ agent.name }}</div>
          <div style="color: var(--color-text-secondary); font-size: 13px;">{{ agent.description }}</div>
          <div style="color: var(--color-text-secondary); font-size: 11px; margin-top: 2px;"><code style="font-size: 11px;">{{ agent.file }}</code></div>
        </div>
        <button onclick="deleteAgent('{{ agent.name }}', '{{ agent.slug }}')" style="padding: 8px 16px; background: none; border: 1px solid #EF4444; border-radius: 8px; font-weight: 600; cursor: pointer; font-size: 13px; font-family: inherit; color: #EF4444;">Delete</button>
      </div>
      {% endfor %}
    </div>
  </div>
</main>

<script>
function switchTab(tab) {
  document.getElementById('panel-design').style.display = tab === 'design' ? 'block' : 'none';
  document.getElementById('panel-agents').style.display = tab === 'agents' ? 'block' : 'none';
  document.getElementById('tab-design').style.color = tab === 'design' ? 'var(--color-primary, #0078D4)' : 'var(--color-text-secondary, #666)';
  document.getElementById('tab-design').style.borderBottomColor = tab === 'design' ? 'var(--color-primary, #0078D4)' : 'transparent';
  document.getElementById('tab-agents').style.color = tab === 'agents' ? 'var(--color-primary, #0078D4)' : 'var(--color-text-secondary, #666)';
  document.getElementById('tab-agents').style.borderBottomColor = tab === 'agents' ? 'var(--color-primary, #0078D4)' : 'transparent';
}

function submitNewDesign() {
  var name = document.getElementById('design-name').value.trim();
  var desc = document.getElementById('design-description').value.trim();
  if (!name || !desc) { alert('Please enter both name and description'); return; }
  var slug = name.toLowerCase().replace(/[^a-z0-9]+/g, '-').replace(/-+$/, '');
  var body = '## Design Request\n\n**Design Name:** ' + name + '\n**Description:**\n' + desc + '\n\n---\n\n### Instructions for Design Specialist Agent\n1. Create a complete new design based on the description above\n2. Rewrite `assets/css/style.css`\n3. Update `_layouts/default.html` and `_layouts/post.html` if needed\n4. Update `index.md` if dashboard layout changes needed\n5. Save the new CSS as `assets/css/themes/' + slug + '.css`\n6. Update `_data/designs.yml` — add new entry, set `active: true`, others `active: false`';
  window.open('https://github.com/shinyay/project-miki/issues/new?title=' + encodeURIComponent('[Design] ' + name) + '&body=' + encodeURIComponent(body) + '&labels=design', '_blank');
}

function applyDesign(name, slug) {
  var body = '## Apply Saved Design\n\n**Design:** ' + name + '\n**Theme file:** `assets/css/themes/' + slug + '.css`\n\n---\n\n### Instructions for Design Specialist Agent\n1. Read saved CSS from `assets/css/themes/' + slug + '.css`\n2. Replace `assets/css/style.css` with the saved CSS\n3. Update `_data/designs.yml` — set `' + name + '` to `active: true`, all others `active: false`';
  window.open('https://github.com/shinyay/project-miki/issues/new?title=' + encodeURIComponent('[Design] Apply: ' + name) + '&body=' + encodeURIComponent(body) + '&labels=design', '_blank');
}

function submitNewAgent() {
  var name = document.getElementById('agent-name').value.trim();
  var desc = document.getElementById('agent-description').value.trim();
  if (!name || !desc) { alert('Please enter both name and description'); return; }
  var slug = name.toLowerCase().replace(/[^a-z0-9]+/g, '-').replace(/-+$/, '');
  var body = '## New Custom Agent Request\n\n**Agent Name:** ' + name + '\n**Description:**\n' + desc + '\n\n---\n\n### Instructions for Agent Creator\nUse the 🛠️ Agent Creator persona (`.github/agents/agent-creator.agent.md`) to:\n1. Create `.github/agents/' + slug + '.agent.md` with full agent definition\n2. Add entry to `_data/agents.yml`\n3. Add to `.github/ISSUE_TEMPLATE/research-request.yml` Persona dropdown\n\nFollow the Agent Creator guidelines for structure, naming, and quality.';
  window.open('https://github.com/shinyay/project-miki/issues/new?title=' + encodeURIComponent('[Agent] Create: ' + name) + '&body=' + encodeURIComponent(body) + '&labels=agent', '_blank');
}

function deleteAgent(name, slug) {
  if (!confirm('Delete agent "' + name + '"?')) return;
  var body = '## Delete Custom Agent\n\n**Agent:** ' + name + '\n**File:** `.github/agents/' + slug + '.agent.md`\n\n---\n\n### Instructions\n1. Delete `.github/agents/' + slug + '.agent.md`\n2. Remove entry for "' + name + '" from `_data/agents.yml`\n3. Remove from `.github/ISSUE_TEMPLATE/research-request.yml` Persona dropdown';
  window.open('https://github.com/shinyay/project-miki/issues/new?title=' + encodeURIComponent('[Agent] Delete: ' + name) + '&body=' + encodeURIComponent(body) + '&labels=agent', '_blank');
}
</script>
