---
layout: default
title: About
permalink: /about/
---

<div class="about-content">

## What is Project Miki?

Project Miki is an intelligence dashboard curated by **GitHub Copilot Coding Agent**. You describe what you want to research in a GitHub Issue, assign it to `@copilot`, and the AI agent curates and publishes a report to this site.

## How to Create a Report

### Step 1: Create a GitHub Issue

Go to [**New Issue →**](https://github.com/shinyay/project-miki/issues/new) and describe what you want to research.

**Example issue descriptions:**

| Example | What You Get |
|---------|-------------|
| "Summarize this week's posts from the Official Microsoft Blog" | Summary of recent Microsoft Corp announcements |
| "What's new in GitHub Copilot? Check the GitHub Blog and Changelog" | Latest Copilot features and updates |
| "Microsoft AI Blog の最新記事をまとめてください" | AI strategy and Copilot updates (in Japanese) |
| "Compare what Microsoft Security Blog and Azure Blog are saying about Zero Trust" | Cross-source thematic analysis |
| "GitHub public roadmap で予定されている新機能を教えて" | Upcoming GitHub features from the roadmap |

### Step 2: Assign to @copilot

Click the **Assignees** gear icon on the right sidebar and type `copilot`. Select the Copilot Coding Agent.

### Step 3: Wait for the PR

Copilot will read your issue, fetch the relevant content, write a report, and open a Pull Request. This usually takes 5-10 minutes.

### Step 4: Merge the PR

Review the report in the PR. If it looks good, click **Merge**. The report will appear on this dashboard within a few minutes.

---

## Available Information Sources

The Coding Agent can fetch real-time content from these domains:

### Microsoft (9 domains)

| Source | URL | Content |
|--------|-----|---------|
| Official Microsoft Blog | blogs.microsoft.com | Executive messages, strategy, partnerships |
| Microsoft On the Issues | blogs.microsoft.com/on-the-issues/ | Brad Smith — policy, governance, AI regulation |
| Microsoft AI Blog | microsoft.com/en-us/ai/blog/ | AI/Copilot strategy, agentic AI |
| Microsoft Dev Blogs | devblogs.microsoft.com | .NET, VS Code, Azure SDK, developer tools |
| Azure Blog | azure.microsoft.com/en-us/blog/ | Cloud, AI/ML, DevOps |
| Microsoft Security Blog | microsoft.com/en-us/security/blog/ | Zero Trust, threat intel, Defender |
| News Center Japan | news.microsoft.com/ja-jp/ | MS Japan news, press releases |
| Windows Blog | blogs.windows.com | Windows, Surface, enterprise |
| Tech Community | techcommunity.microsoft.com | Product teams, community discussions |

### GitHub (4 domains)

| Source | URL | Content |
|--------|-----|---------|
| GitHub Blog | github.blog | Official announcements, Copilot, engineering |
| GitHub Changelog | github.blog/changelog/ | New releases, improvements, deprecations |
| GitHub Docs | docs.github.com | Product documentation, API reference |
| GitHub Universe | githubuniverse.com | Annual conference, keynotes |

---

## プロジェクトについて (Japanese)

Project Mikiは、**GitHub Copilot Coding Agent**がキュレーションするインテリジェンスダッシュボードです。

### レポートの作成方法

1. **Issueを作成** — [新しいIssue →](https://github.com/shinyay/project-miki/issues/new) で調べたい内容を記述
2. **@copilotに割り当て** — Assigneesで「copilot」を選択
3. **PRを待つ** — Copilotが内容を取得・要約してPRを作成（5〜10分）
4. **マージ** — PRをマージすると、このダッシュボードに表示されます

### Issue の記述例

- 「Microsoft公式ブログの今週の記事をまとめてください」
- 「GitHub Copilotの最新アップデートを教えて」
- 「Azure BlogとSecurity Blogのゼロトラスト関連記事を比較して」
- 「GitHub Changelogの最新リリースをまとめて」

</div>
