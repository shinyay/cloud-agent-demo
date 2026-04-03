---
layout: default
title: About
permalink: /about/
---

<section class="about-hero">
  <div class="container">
    <h2 class="about-hero-title">About Copilot Pulse</h2>
    <p class="about-hero-subtitle">An intelligence dashboard curated by GitHub Copilot Cloud Agent — describe what you want to research in a GitHub Issue, assign it to <code>@copilot</code>, and the AI agent curates and publishes a report to this site.</p>
  </div>
</section>

<div class="about-content container">

  <!-- How it works -->
  <section class="about-section">
    <h2 class="about-section-title">🚀 How to Create a Report</h2>
    <ol class="step-list">
      <li>
        <strong>Create a GitHub Issue</strong><br>
        Go to <a href="https://github.com/shinyay/cloud-agent-demo/issues/new?template=research-request.yml" target="_blank">New Report →</a> and fill out the structured form — research topic, persona (specialist), detail level, tone, language, information sources, and any additional instructions.
      </li>
      <li>
        <strong>Assign to @copilot</strong><br>
        Click the <strong>Assignees</strong> gear icon on the right sidebar, type <code>copilot</code>, and select the Copilot Cloud Agent.
      </li>
      <li>
        <strong>Wait for the PR</strong><br>
        Copilot reads your issue, fetches the relevant content, writes a report, and opens a Pull Request. This usually takes 5–10 minutes.
      </li>
      <li>
        <strong>Merge the PR</strong><br>
        Review the report in the PR. If it looks good, click <strong>Merge</strong>. The report will appear on this dashboard within a few minutes.
      </li>
    </ol>
  </section>

  <!-- Sources -->
  <section class="about-section">
    <h2 class="about-section-title">📡 Available Information Sources</h2>
    <p class="about-section-desc">The Cloud Agent can fetch real-time content from these domains:</p>

    <div class="source-grid">
      <div class="source-group">
        <h3 class="source-group-title"><span class="source-icon">Ⓜ</span> Microsoft <span class="source-count">9 sources</span></h3>
        <div class="source-cards">
          <div class="source-card">
            <div class="source-card-name">Official Microsoft Blog</div>
            <div class="source-card-url">blogs.microsoft.com</div>
            <div class="source-card-desc">Executive messages, strategy, partnerships</div>
          </div>
          <div class="source-card">
            <div class="source-card-name">Microsoft On the Issues</div>
            <div class="source-card-url">blogs.microsoft.com/on-the-issues/</div>
            <div class="source-card-desc">Brad Smith — policy, governance, AI regulation</div>
          </div>
          <div class="source-card">
            <div class="source-card-name">Microsoft AI Blog</div>
            <div class="source-card-url">microsoft.com/en-us/ai/blog/</div>
            <div class="source-card-desc">AI/Copilot strategy, agentic AI</div>
          </div>
          <div class="source-card">
            <div class="source-card-name">Microsoft Dev Blogs</div>
            <div class="source-card-url">devblogs.microsoft.com</div>
            <div class="source-card-desc">.NET, VS Code, Azure SDK, developer tools</div>
          </div>
          <div class="source-card">
            <div class="source-card-name">Azure Blog</div>
            <div class="source-card-url">azure.microsoft.com/en-us/blog/</div>
            <div class="source-card-desc">Cloud, AI/ML, DevOps</div>
          </div>
          <div class="source-card">
            <div class="source-card-name">Microsoft Security Blog</div>
            <div class="source-card-url">microsoft.com/en-us/security/blog/</div>
            <div class="source-card-desc">Zero Trust, threat intel, Defender</div>
          </div>
          <div class="source-card">
            <div class="source-card-name">News Center Japan</div>
            <div class="source-card-url">news.microsoft.com/ja-jp/</div>
            <div class="source-card-desc">MS Japan news, press releases</div>
          </div>
          <div class="source-card">
            <div class="source-card-name">Windows Blog</div>
            <div class="source-card-url">blogs.windows.com</div>
            <div class="source-card-desc">Windows, Surface, enterprise</div>
          </div>
          <div class="source-card">
            <div class="source-card-name">Tech Community</div>
            <div class="source-card-url">techcommunity.microsoft.com</div>
            <div class="source-card-desc">Product teams, community discussions</div>
          </div>
        </div>
      </div>

      <div class="source-group">
        <h3 class="source-group-title"><span class="source-icon">🐙</span> GitHub <span class="source-count">4 sources</span></h3>
        <div class="source-cards">
          <div class="source-card">
            <div class="source-card-name">GitHub Blog</div>
            <div class="source-card-url">github.blog</div>
            <div class="source-card-desc">Official announcements, Copilot, engineering</div>
          </div>
          <div class="source-card">
            <div class="source-card-name">GitHub Changelog</div>
            <div class="source-card-url">github.blog/changelog/</div>
            <div class="source-card-desc">New releases, improvements, deprecations</div>
          </div>
          <div class="source-card">
            <div class="source-card-name">GitHub Docs</div>
            <div class="source-card-url">docs.github.com</div>
            <div class="source-card-desc">Product documentation, API reference</div>
          </div>
          <div class="source-card">
            <div class="source-card-name">GitHub Universe</div>
            <div class="source-card-url">githubuniverse.com</div>
            <div class="source-card-desc">Annual conference, keynotes</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Report form fields -->
  <section class="about-section">
    <h2 class="about-section-title">📝 Report Request Form</h2>
    <p class="about-section-desc">When creating a new report issue, you can customize these fields:</p>
    <div class="form-fields-grid">
      <div class="form-field-card">
        <div class="form-field-name">Research Topic</div>
        <div class="form-field-desc">What do you want to know?</div>
      </div>
      <div class="form-field-card">
        <div class="form-field-name">Persona</div>
        <div class="form-field-desc">Microsoft Specialist, GitHub Specialist, Executive Analyst, News Curator, Japan Market Specialist, and more</div>
      </div>
      <div class="form-field-card">
        <div class="form-field-name">Detail Level</div>
        <div class="form-field-desc">Brief, Standard, or Detailed</div>
      </div>
      <div class="form-field-card">
        <div class="form-field-name">Tone</div>
        <div class="form-field-desc">Executive Briefing, Journalistic, Analytical, Technical, Casual, Academic, or Strategic</div>
      </div>
      <div class="form-field-card">
        <div class="form-field-name">Report Language</div>
        <div class="form-field-desc">English, Japanese, or Auto</div>
      </div>
      <div class="form-field-card">
        <div class="form-field-name">Information Sources</div>
        <div class="form-field-desc">Select which Microsoft/GitHub sources to check</div>
      </div>
      <div class="form-field-card">
        <div class="form-field-name">Additional Instructions</div>
        <div class="form-field-desc">Any special focus or context</div>
      </div>
    </div>
  </section>

  <!-- Japanese section -->
  <section class="about-section about-jp">
    <h2 class="about-section-title">🇯🇵 プロジェクトについて</h2>
    <p>Copilot Pulseは、<strong>GitHub Copilot Cloud Agent</strong>がキュレーションするインテリジェンスダッシュボードです。</p>

    <h3 class="about-subsection-title">レポートの作成方法</h3>
    <ol class="step-list">
      <li>
        <strong>Issueを作成</strong><br>
        <a href="https://github.com/shinyay/cloud-agent-demo/issues/new?template=research-request.yml" target="_blank">新しいIssue →</a> で調べたい内容を記述
      </li>
      <li>
        <strong>@copilotに割り当て</strong><br>
        Assigneesで「copilot」を選択
      </li>
      <li>
        <strong>PRを待つ</strong><br>
        Copilotが内容を取得・要約してPRを作成（5〜10分）
      </li>
      <li>
        <strong>マージ</strong><br>
        PRをマージすると、このダッシュボードに表示されます
      </li>
    </ol>

    <h3 class="about-subsection-title">Issue の記述例</h3>
    <div class="example-queries">
      <div class="example-query">「Microsoft公式ブログの今週の記事をまとめてください」</div>
      <div class="example-query">「GitHub Copilotの最新アップデートを教えて」</div>
      <div class="example-query">「Azure BlogとSecurity Blogのゼロトラスト関連記事を比較して」</div>
      <div class="example-query">「GitHub Changelogの最新リリースをまとめて」</div>
    </div>
  </section>

</div>
