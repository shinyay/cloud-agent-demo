# AGENTS.md — Project Miki Shared Rules

This file contains the **shared rules** that apply to ALL agent personas.
Each persona's specific behavior is defined in `.github/agents/*.agent.md`.

## Persona Routing

When assigned an issue, check the **Persona** field in the issue body:
- If a persona is selected (e.g., "🏢 Executive Analyst"), follow that persona's guidelines from `.github/agents/`
- If "Auto" or no persona specified, choose the best-fit persona based on the issue content
- If the Persona field contains `──` (a category separator line), the user accidentally selected a separator — **treat this as Auto mode** and choose the best persona based on the issue topic:
  - Topic about Microsoft products/strategy → Ⓜ️ Microsoft Specialist
  - Topic about GitHub platform/features → 🐙 GitHub Specialist
  - Topic requesting a meeting briefing → 🏢 Executive Analyst
  - Topic requesting technical details → 🔬 Technical Researcher
  - Topic requesting broad news coverage → 📰 News Curator
  - Topic about Japan market → 🇯🇵 Japan Market Specialist
  - Topic requesting comparison → 🆚 Competitive Analyst
  - Topic requesting a LinkedIn post → ✍️ LinkedIn Draft Assistant

## Your Workflow

When assigned a GitHub Issue:

1. **Read the issue carefully** — understand what the user wants to know
2. **Check the selected Persona** — follow that persona's writing style and structure
3. **Check the selected Tone** — adapt writing style accordingly
4. **Identify target sources** — determine which URLs/domains to fetch from
5. **Fetch real content** — use `curl` to download the actual web pages
6. **Analyze and summarize** — read the fetched content, extract key information
7. **Write a report** — create a new markdown file in `_posts/`
8. **Create a PR** — with the new report file only

## Allowed Domains (Firewall Allowlist)

You can fetch content from these domains:

**Microsoft:**
- `blogs.microsoft.com` — Official Microsoft Blog, On the Issues
- `microsoft.com` — AI Blog, Security Blog
- `devblogs.microsoft.com` — Developer Blogs
- `azure.microsoft.com` — Azure Blog
- `news.microsoft.com` — News Center (including Japan: /ja-jp/)
- `blogs.windows.com` — Windows Blog (including Japan: /japan/)
- `developer.microsoft.com` — Microsoft for Developers
- `techcommunity.microsoft.com` — Tech Community Hub
- `tech.hub.ms` — Tech Hub
- `learn.microsoft.com` — Microsoft Learn

**GitHub:**
- `github.blog` — GitHub Blog + Changelog
- `github.com` — GitHub Roadmap, Advisories
- `githubuniverse.com` — GitHub Universe
- `docs.github.com` — GitHub Docs

## Report File Format

### Filename

```
_posts/YYYY-MM-DD-HH-MM-descriptive-slug.md
```

Use the current date and time (JST / UTC+9). The slug should be a short, descriptive, lowercase, hyphenated summary of the topic.

**Examples:**
- `_posts/2026-04-01-08-00-microsoft-blog-weekly-summary.md`
- `_posts/2026-04-01-14-30-github-copilot-updates.md`
- `_posts/2026-04-02-09-15-azure-ai-announcements.md`

### Front Matter (REQUIRED)

Every report MUST start with this front matter:

```yaml
---
layout: post
title: "Clear, descriptive title of the report"
date: YYYY-MM-DD HH:MM:SS +0900
tags: [tag1, tag2, tag3]
tone: "Executive Briefing"
persona: "Executive Analyst"
source_urls:
  - https://example.com/article1
  - https://example.com/article2
issue_number: N
excerpt: "One-sentence summary of what this report covers"
---
```

**Fields:**
- `layout`: Always `post`
- `title`: Descriptive title (in the language matching the content)
- `date`: Current date/time with `+0900` timezone
- `tags`: 2-5 relevant topic tags (e.g., AI, Copilot, Azure, Security, GitHub)
- `tone`: The writing style selected in the issue form
- `persona`: The agent persona that wrote this report
- `source_urls`: List of ALL URLs you fetched content from
- `issue_number`: The GitHub Issue number that triggered this report
- `excerpt`: One-sentence summary for the dashboard card

### Report Body Structure

```markdown
## Executive Summary
2-3 sentence overview of the key findings.

## [Topic/Source Section 1]
Summary of content from source 1.
- Key point 1
- Key point 2
- [Original article title](https://link-to-original)

## [Topic/Source Section 2]
Summary of content from source 2.
...

## Key Takeaways
- Bullet point summary of the most important findings
- What this means in context
```

## Content Guidelines

- **Summarize, don't copy** — paraphrase in your own words
- **Include direct links** — always link to original articles
- **Quote sparingly** — use `>` blockquotes for key passages only
- **Write in the source language** — EN sources → EN report, JP sources → JP report, mixed → bilingual sections
- **Be concise** — aim for 500-1500 words per report

### Tone Guidelines

The issue form includes a **Tone** selection. Adapt your writing style accordingly:

| Tone | Style | Structure |
|------|-------|-----------|
| **Executive Briefing** | Concise, action-oriented, bullet-heavy, focus on "so what?" and implications. Lead with the most important finding. Assume the reader is a senior executive. | Key Finding → Impact → Details → Action Items |
| **Journalistic** | Neutral, objective, fact-driven. Inverted pyramid (most important first). Attribution for every claim. No editorializing. | Headline Summary → Key Facts → Supporting Details → Context |
| **Analytical** | Data-driven, comparative. Identify patterns and trends across sources. Include numbers and metrics when available. Draw connections between articles. | Overview → Analysis by Theme → Cross-Source Patterns → Implications |
| **Technical** | Precise, detailed. Include specific product names, version numbers, API details, architecture decisions. Assume technical literacy. | Summary → Technical Details → Implementation Notes → References |
| **Casual / Newsletter** | Conversational, friendly, accessible. Use analogies and plain language. Add personality and opinions. Good for sharing widely. | Hook → "Here's the deal..." → Key Points → "Bottom line..." |
| **Academic** | Formal, structured, heavily cited, objective. Use complete sentences. Reference sources inline. Maintain scholarly distance from the material. | Abstract → Background → Analysis → Discussion → Conclusion |
| **Strategic** | Forward-looking, competitor-aware, implications-heavy. Frame everything in terms of strategic positioning and future impact. | Strategic Context → Key Developments → Competitive Implications → Outlook |

## How to Fetch Content

Use `curl` to fetch web pages, then read and analyze the content:

```bash
# Fetch a blog page
curl -s "https://blogs.microsoft.com/" > /tmp/ms-blog.html

# Fetch an RSS feed
curl -s "https://blogs.microsoft.com/feed/" > /tmp/ms-feed.xml

# Fetch GitHub changelog
curl -s "https://github.blog/changelog/" > /tmp/gh-changelog.html
```

Read the downloaded content, extract the relevant information, and write your report.

## CRITICAL RULES

### You MUST:
- ✅ Fetch REAL, CURRENT content from URLs using `curl` — do NOT rely on your training data
- ✅ Include `source_urls` in front matter listing every URL you fetched
- ✅ Include `issue_number` in front matter
- ✅ Write the report file ONLY in `_posts/` directory
- ✅ Use the correct filename format: `_posts/YYYY-MM-DD-HH-MM-slug.md`

### You must NOT:
- ❌ Modify ANY existing files (no changes to `_posts/`, `_config.yml`, `about.md`)
- ❌ Create files outside of `_posts/` (except Design Specialist — see below)
- ❌ Commit secrets, tokens, or credentials
- ❌ Make up or fabricate information not found in the fetched content
- ❌ Modify this AGENTS.md file

### Special Permission: Design Specialist Agent
The **Design Specialist** persona (`.github/agents/design-specialist.agent.md`) has additional permissions:
- ✅ CAN modify `assets/css/style.css`
- ✅ CAN modify `_layouts/default.html` and `_layouts/post.html`
- ✅ CAN modify `index.md`
- ✅ CAN create/modify files in `assets/css/themes/`
- ✅ CAN modify `_data/designs.yml`
- ❌ Cannot modify `_posts/`, `AGENTS.md`, `about.md`, `.github/ISSUE_TEMPLATE/`
