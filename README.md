# 📊 Project Miki — Intelligence Dashboard

An intelligence dashboard powered by **GitHub Copilot Coding Agent**. Describe what you want to research in a GitHub Issue, assign it to `@copilot`, and get a curated report published to GitHub Pages.

## How It Works

```
1. Create a GitHub Issue → describe what you want to know
2. Assign to @copilot
3. Copilot fetches content, summarizes, writes a report
4. Merge the PR → report appears on the dashboard
```

**🌐 Dashboard:** [shinyay.github.io/project-miki](https://shinyay.github.io/project-miki/)

## Quick Start

1. Go to [**Issues → New Issue**](https://github.com/shinyay/project-miki/issues/new)
2. Write what you want to research, for example:
   - "Summarize this week's Official Microsoft Blog posts"
   - "GitHub Copilot の最新アップデートをまとめて"
   - "What's new in Azure AI this month?"
3. Assign to **@copilot** (Assignees → type "copilot")
4. Wait 5-10 minutes for the PR
5. Merge → dashboard updates automatically

## Available Sources

The Coding Agent can fetch from **13 Microsoft + GitHub domains**:

| Category | Domains |
|----------|---------|
| **Microsoft** | blogs.microsoft.com, microsoft.com, devblogs.microsoft.com, azure.microsoft.com, news.microsoft.com, blogs.windows.com, developer.microsoft.com, techcommunity.microsoft.com, tech.hub.ms |
| **GitHub** | github.blog, github.com, githubuniverse.com, docs.github.com |

## Architecture

```
GitHub Issue (user writes research request)
    ↓
@copilot assigned (Coding Agent activates)
    ↓
Agent fetches content from allowed domains via curl
    ↓
Agent writes _posts/YYYY-MM-DD-HH-MM-slug.md
    ↓
PR created → user merges
    ↓
GitHub Pages auto-deploys (Jekyll renders markdown → HTML)
    ↓
Report visible on dashboard
```

## Project Structure

```
project-miki/
├── _config.yml          ← Jekyll configuration
├── _layouts/
│   ├── default.html     ← Dashboard layout
│   └── post.html        ← Report layout
├── _posts/              ← Reports (written by Copilot)
│   └── YYYY-MM-DD-HH-MM-slug.md
├── assets/css/style.css ← Styling
├── index.md             ← Dashboard home (auto-lists reports)
├── about.md             ← Usage guide + source list
├── AGENTS.md            ← Instructions for Coding Agent
├── .github/
│   └── copilot-setup-steps.yml
└── README.md
```

## License

MIT
