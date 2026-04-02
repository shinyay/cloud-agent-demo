# 📊 Project Miki — Intelligence Dashboard

An intelligence dashboard powered by **GitHub Copilot Coding Agent**. Describe what you want to research in a GitHub Issue, assign it to `@copilot`, and get a curated report published to GitHub Pages.

## How It Works

```
1. Create a GitHub Issue → select persona, tone, sources
2. Assign to @copilot
3. Copilot fetches content, summarizes, writes a report
4. Merge the PR → report appears on the dashboard
```

**🌐 Dashboard:** [shinyay.github.io/project-miki](https://shinyay.github.io/project-miki/)

## Quick Start

1. Go to [**Issues → New Issue**](https://github.com/shinyay/project-miki/issues/new?template=research-request.yml)
2. Fill in the structured form:
   - **Topic** — what you want to know
   - **Persona** — which AI specialist should write it (10 options)
   - **Tone** — writing style (7 options: Executive Briefing, Journalistic, Analytical, etc.)
   - **Language** — Japanese, English, or bilingual
3. Assign to **@copilot** (Assignees → type "copilot")
4. Wait 5-10 minutes for the PR
5. Merge → dashboard updates automatically

## Agent Personas (10)

| Persona | Description |
|---------|-------------|
| 🤖 Auto | Automatically picks the best-fit persona |
| Ⓜ️ Microsoft Specialist | Deep Microsoft domain expertise |
| 🐙 GitHub Specialist | Deep GitHub/developer ecosystem expertise |
| 🏢 Executive Analyst | Strategic implications and action items |
| 🔬 Technical Researcher | Specs, APIs, architecture details |
| 📰 News Curator | Broad coverage, many articles briefly |
| 🇯🇵 Japan Market Specialist | Bilingual, Japan market context |
| 🆚 Competitive Analyst | Cross-source comparison |
| ✍️ LinkedIn Draft Assistant | Ready-to-post LinkedIn drafts |
| 🎨 Design Specialist | Frontend design, CSS, layouts |

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
Agent fetches content via RSS feeds + HTML from allowed domains
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
├── _config.yml              ← Jekyll configuration
├── _layouts/
│   ├── default.html         ← Dashboard layout (nav, header, footer)
│   └── post.html            ← Report layout (progress bar, tags, sources)
├── _posts/                  ← Reports (written by Copilot)
│   └── YYYY-MM-DD-HH-MM-slug.md
├── assets/css/
│   ├── style.css            ← Main stylesheet (dark mode, glassmorphism)
│   └── themes/              ← Saved design themes
├── _data/
│   ├── agents.yml           ← Agent registry
│   └── designs.yml          ← Design theme registry
├── .github/
│   ├── agents/              ← Custom agent definitions (*.agent.md)
│   ├── ISSUE_TEMPLATE/      ← Report request form
│   └── workflows/           ← Auto-title workflow
├── index.md                 ← Dashboard home
├── about.md                 ← Usage guide + source list
├── archive.md               ← Full report archive
├── admin.md                 ← Admin: design & agent management
├── AGENTS.md                ← Instructions for Coding Agent
└── README.md
```

## Admin Page

Visit [/admin/](https://shinyay.github.io/project-miki/admin/) to:
- 🎨 **Manage designs** — create new themes, switch between saved themes
- 🤖 **Manage agents** — view registered agents, create new custom agents

## License

MIT
