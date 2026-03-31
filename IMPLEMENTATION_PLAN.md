# Phase 1 Implementation Plan — Smart RSS Reader

> **Project:** Strategic Narrative Diff (Project Miki)
> **Phase:** 1 of 5
> **Goal:** Working app that polls executive blogs, extracts AI summaries, and delivers email digests
> **Execution:** GitHub Issues assigned to Copilot Coding Agent (`@copilot`)

## Prerequisites

| Requirement | How to Set Up |
|------------|---------------|
| GitHub Copilot subscription (Pro+ / Business / Enterprise) | github.com/settings/copilot |
| Coding agent enabled for the repo | Repo Settings → Copilot → Enable coding agent |
| PostgreSQL 16+ running locally or hosted | `docker run -p 5432:5432 -e POSTGRES_PASSWORD=dev pgvector/pgvector:pg16` |
| `GITHUB_TOKEN` environment variable | Your GitHub PAT with Copilot access |
| `SND_SENDGRID_API_KEY` environment variable | sendgrid.com → API Keys |
| `SND_DATABASE_URL` environment variable | `postgresql://postgres:dev@localhost:5432/snd` |

## Issue Dependency Chain

```
P1-01 (Project scaffolding)
  └──► P1-02 (Database migration)
         └──► P1-03 (Config loading)
                └──► P1-04 (SQLAlchemy models)
                       ├──► P1-05 (RSS poller)
                       │      └──► P1-07 (Collection pipeline)
                       ├──► P1-06 (Web extractor)
                       │      └──► P1-07 (Collection pipeline)
                       └──► P1-08 (Copilot SDK client)
                              └──► P1-09 (Theme extraction)
                                     └──► P1-10 (Digest assembler)
                                            └──► P1-11 (MJML template)
                                                   └──► P1-12 (SendGrid sender)
                                                          └──► P1-13 (APScheduler)
                                                                 └──► P1-14 (Entrypoint)
                                                                        └──► P1-15 (Smoke test)
```

## Assignment Order

Assign issues to `@copilot` **one at a time** in this order. Wait for each PR to be merged before assigning the next (unless issues are independent).

**Parallel-safe pairs** (can be assigned simultaneously):
- P1-05 + P1-06 (both depend on P1-04, independent of each other)
- P1-05 + P1-08 (both depend on P1-04, independent of each other)

## Directory Structure (Created by P1-01)

```
project-miki/
├── src/
│   └── snd/
│       ├── __init__.py
│       ├── main.py
│       ├── config.py
│       ├── database.py
│       ├── models/
│       │   ├── __init__.py
│       │   ├── executive.py
│       │   ├── source.py
│       │   ├── post.py
│       │   ├── theme.py
│       │   └── digest.py
│       ├── services/
│       │   ├── __init__.py
│       │   ├── collector.py
│       │   ├── extractor.py
│       │   ├── analyzer.py
│       │   ├── llm_client.py
│       │   └── email.py
│       ├── pipelines/
│       │   ├── __init__.py
│       │   ├── collection.py
│       │   └── digest.py
│       └── templates/
│           └── digest.mjml
├── alembic/
│   ├── alembic.ini
│   ├── env.py
│   └── versions/
├── tests/
│   ├── __init__.py
│   ├── conftest.py
│   └── cassettes/
├── config.yaml
├── pyproject.toml
├── SPEC.md
├── IMPLEMENTATION_PLAN.md
├── AGENTS.md
└── README.md
```

---

## Issue Details

### P1-01: Project Scaffolding

**Task:** Create the Python project structure with pyproject.toml and all directory/file stubs.

**Files to create:**
- `pyproject.toml` — with dependencies: feedparser, trafilatura, httpx, sqlalchemy[asyncio], alembic, psycopg2-binary, pgvector, pydantic, pydantic-settings, structlog, apscheduler, sendgrid, langdetect, mjml (or mjml-python), ruff (dev), pytest (dev), pytest-asyncio (dev), vcrpy (dev)
- All directories and `__init__.py` files per the directory structure above
- All `.py` files as empty stubs with module docstrings

**Acceptance Criteria:**
- [ ] `pip install -e ".[dev]"` succeeds without errors
- [ ] `python -c "import snd"` works
- [ ] `ruff check src/` passes (no errors on empty files)
- [ ] Directory structure matches the plan exactly

**Ref:** SPEC.md Section 8 (Technology Stack)

---

### P1-02: Database Setup — Alembic + Phase 1 Migration

**Task:** Initialize Alembic and create the first migration with Phase 1 tables.

**Files to create/modify:**
- `alembic.ini` — configured for `SND_DATABASE_URL` env var
- `alembic/env.py` — imports SQLAlchemy models, reads DB URL from env
- `alembic/versions/001_phase1_tables.py` — migration creating:
  - Enum types: `seniority_type`, `source_status`, `processing_status`, `stance_type`, `prominence_type`, `framing_type`, `specificity_type`, `digest_status`
  - Tables: `executives`, `sources`, `posts`, `themes`, `post_themes`, `digests`
  - All indexes per SPEC.md Section 10.2
  - pgvector extension: `CREATE EXTENSION IF NOT EXISTS vector`
  - `updated_at` trigger function

**Acceptance Criteria:**
- [ ] `alembic upgrade head` runs successfully against a fresh PostgreSQL database
- [ ] `alembic downgrade base` cleanly drops all tables
- [ ] All 6 tables exist with correct columns, types, and constraints
- [ ] pgvector `vector(1536)` column exists on `themes` table
- [ ] HNSW index exists on `themes.embedding`

**Ref:** SPEC.md Section 10.1, 10.2 (full DDL provided)

---

### P1-03: Configuration Loading

**Task:** Implement YAML config loading with Pydantic validation and environment variable overrides.

**Files to create:**
- `src/snd/config.py` — Pydantic Settings models:
  - `ExecutiveConfig` — name, organization, role, language, seniority, sources[], active
  - `SourceConfig` — type, url, check_interval_hours, scrape_config
  - `ScheduleConfig` — cron, timezone, no_change_email
  - `RecipientConfig` — email, name, language
  - `AnalysisConfig` — sensitivity, max_signals_per_digest, backfill_limit
  - `LLMConfig` — provider, primary_model, secondary_model, embedding_provider, embedding_model, temperature, max_retries
  - `EmailConfig` — provider, from_address, from_name
  - `DatabaseConfig` — url, pool_size
  - `AppConfig` — top-level combining all above
  - `load_config(path: str) -> AppConfig` function
- `config.yaml` — example config with 3 real executive sources:
  1. NEC Corporate Blog (`jpn.nec.com/corporateblog/`)
  2. Google Japan Blog (`blog.google/intl/ja-jp/`)
  3. Salesforce Japan Blog (`salesforce.com/jp/blog/recent-stories/`)

**Acceptance Criteria:**
- [ ] `load_config("config.yaml")` returns a valid `AppConfig` instance
- [ ] Missing required fields raise `ValidationError` with clear message
- [ ] `SND_DATABASE_URL` env var overrides `database.url` in YAML
- [ ] Default values applied for all optional fields
- [ ] Config file is self-documenting with comments

**Ref:** SPEC.md FR-11 (Section 9, FR-11), Section 15

---

### P1-04: SQLAlchemy ORM Models

**Task:** Create SQLAlchemy 2.0 ORM models for all Phase 1 tables.

**Files to create:**
- `src/snd/database.py` — async engine factory, session factory, `get_db()` dependency
- `src/snd/models/__init__.py` — re-export all models
- `src/snd/models/executive.py` — `Executive` model
- `src/snd/models/source.py` — `Source` model
- `src/snd/models/post.py` — `Post` model
- `src/snd/models/theme.py` — `Theme` model (with pgvector `Vector(1536)` column), `PostTheme` model
- `src/snd/models/digest.py` — `Digest` model

**Requirements:**
- Use SQLAlchemy 2.0 declarative style with `mapped_column()`
- Use `pgvector.sqlalchemy.Vector` for embedding columns
- Define relationships (e.g., `Executive.sources`, `Post.themes`, `Post.executive`)
- All enums as SQLAlchemy `Enum` types matching the PostgreSQL enums from P1-02

**Acceptance Criteria:**
- [ ] All 6 models importable: `from snd.models import Executive, Source, Post, Theme, PostTheme, Digest`
- [ ] Models match the DDL schema in SPEC.md Section 10.2 exactly
- [ ] Relationships correctly defined (e.g., `executive.posts` returns related posts)
- [ ] `Vector(1536)` column on Theme model works with pgvector

**Ref:** SPEC.md Section 10.2, 10.3

---

### P1-05: RSS Feed Poller

**Task:** Implement RSS feed polling with feedparser, entry extraction, and URL deduplication.

**Files to create:**
- `src/snd/services/collector.py` — `RSSPoller` class:
  - `async def poll(source: Source) -> list[FeedEntry]`
  - `FeedEntry` Pydantic model: url, title, published_at, guid
  - Parse RSS/Atom feeds using feedparser
  - Extract: guid (or link as fallback), title, published date
  - Handle malformed feeds gracefully (log warning, return empty list)
- `tests/test_collector.py` — test with a recorded RSS fixture

**Acceptance Criteria:**
- [ ] Successfully parses a real RSS feed (e.g., `blogs.microsoft.com/feed/`)
- [ ] Returns `FeedEntry` list with url, title, published_at for each entry
- [ ] Handles malformed or empty feeds without crashing
- [ ] Test passes with a VCR-recorded fixture

**Ref:** SPEC.md FR-2 (Content Collection)

---

### P1-06: Web Content Extractor

**Task:** Implement content extraction from web pages using trafilatura and httpx.

**Files to create:**
- `src/snd/services/extractor.py` — `ContentExtractor` class:
  - `async def extract(url: str) -> ExtractedContent | None`
  - `ExtractedContent` Pydantic model: title, full_text, published_at, thumbnail_url, language, word_count, author
  - Fetch page with httpx (async, 30s timeout)
  - Extract with trafilatura (output_format='json', include_metadata=True, favor_precision=True)
  - Extract og:image for thumbnail
  - Detect language with langdetect
  - Handle extraction failures (return None, log warning)

**Acceptance Criteria:**
- [ ] Extracts clean text from a real blog URL (e.g., an NEC Stories article)
- [ ] Returns title, full_text (no HTML), published_at, thumbnail_url
- [ ] Language detection returns 'en' or 'ja' correctly
- [ ] Returns None for unreachable URLs (no crash)
- [ ] Word count is calculated correctly

**Ref:** SPEC.md FR-2 (Content Collection), code example in FR-2

---

### P1-07: Collection Pipeline Orchestrator

**Task:** Combine RSS poller + content extractor into a complete collection pipeline.

**Files to create:**
- `src/snd/pipelines/collection.py` — `CollectionPipeline` class:
  - `async def run(config: AppConfig, db: AsyncSession) -> CollectionResult`
  - `CollectionResult` Pydantic model: sources_checked, new_posts, errors, duration_seconds
  - For each active source in config:
    1. Check if source is due for polling (based on check_interval_hours + last_checked_at)
    2. If RSS: poll → get entry URLs → dedup against posts table → extract content for new URLs
    3. Store new posts in database with `processing_status='pending'`
    4. Update source `last_checked_at` and `last_success_at`
  - Error handling: 3x retry with exponential backoff (2s, 8s, 32s) per source
  - Skip failed sources (don't block others)
  - Structured logging for every step

**Acceptance Criteria:**
- [ ] Polls all active sources and stores new posts in the database
- [ ] Deduplicates by URL (same URL never stored twice)
- [ ] Failed sources don't block other sources
- [ ] `CollectionResult` shows accurate counts
- [ ] Structured log entries for: collection_started, source_polled, post_stored, source_failed, collection_completed

**Ref:** SPEC.md FR-2, Section 7.1 (Collection Pipeline sequence diagram)

---

### P1-08: Copilot SDK Client Wrapper

**Task:** Create a wrapper around the GitHub Copilot SDK with structured output support via Pydantic validation + retry.

**Files to create:**
- `src/snd/services/llm_client.py` — `LLMClient` class:
  - `__init__(primary_model: str, secondary_model: str)`
  - `async def complete(prompt: str, system_prompt: str, model: str = "primary", response_model: type[BaseModel] | None = None) -> str | BaseModel`
  - If `response_model` is provided:
    1. Append JSON schema instructions to prompt
    2. Send via Copilot SDK session
    3. Parse response with `response_model.model_validate_json()`
    4. On validation failure: retry up to `max_retries` times with error feedback in prompt
    5. Return validated Pydantic instance
  - If no `response_model`: return raw string response
  - Session management: create session per call (or reuse if possible)
  - Timeout handling: 30s default
  - Structured logging: log model used, token estimate, latency

**Acceptance Criteria:**
- [ ] `complete(prompt, system_prompt)` returns a string response
- [ ] `complete(prompt, system_prompt, response_model=MyModel)` returns a validated Pydantic instance
- [ ] Retries on validation failure with error message in prompt
- [ ] Raises `LLMError` after max_retries exhausted
- [ ] Logs model, latency, and success/failure for every call

**Ref:** SPEC.md Section 11.5 (Pydantic schemas), Section 11.6 (Model selection)

---

### P1-09: Theme Extraction Service

**Task:** Implement LLM-based theme extraction using the Copilot SDK client and SPEC.md prompts.

**Files to create:**
- `src/snd/services/analyzer.py` — `ThemeAnalyzer` class:
  - `async def extract_themes(post: Post) -> ThemeExtractionResult`
  - Uses `LLMClient.complete()` with `response_model=ThemeExtractionResult`
  - System prompt from SPEC.md Section 11.1 (English) + 11.2 (Japanese supplement if `post.language == 'ja'`)
  - User prompt template: includes executive name, org, post title, post text, date
  - Stores extracted themes in `post_themes` table
  - Creates new entries in `themes` table for unseen themes
  - Updates `post.processing_status` to 'analyzed' (or 'failed')
  - Pydantic models needed (from SPEC.md 11.5): `PostTheme`, `ExtractedClaim`, `ThemeExtractionResult`

**Acceptance Criteria:**
- [ ] Returns `ThemeExtractionResult` with 1-6 themes for a real blog post
- [ ] Each theme has: label_en, stance, prominence, framing, evidence_quote
- [ ] Post `processing_status` updated to 'analyzed' after success
- [ ] Japanese posts include `label_ja` in addition to `label_en`
- [ ] Handles LLM failure gracefully (marks post as 'failed', logs error)

**Ref:** SPEC.md FR-3, Section 11.1, 11.2, 11.5

---

### P1-10: Digest Content Assembler

**Task:** Query recent posts and assemble the digest data structure.

**Files to create:**
- `src/snd/pipelines/digest.py` — `DigestPipeline` class (Phase 1 portion):
  - `async def assemble(config: AppConfig, db: AsyncSession) -> DigestContent`
  - `DigestContent` Pydantic model (Phase 1 simplified):
    - `executive_cards: list[ExecutiveCard]`
    - `metadata: dict` (exec_count, post_count, period)
  - `ExecutiveCard` (Phase 1):
    - executive_name, organization, role, thumbnail_url
    - recent_posts: list of {title, url, summary, published_at, themes}
  - Query: all posts collected since last digest, grouped by executive
  - For each executive: build a card with their recent posts and extracted themes
  - Sort by post count (most active executives first)
  - Limit to `config.analysis.max_executive_cards` (default 10)

**Acceptance Criteria:**
- [ ] Returns `DigestContent` with executive cards containing recent posts
- [ ] Posts are grouped by executive
- [ ] Each post includes title, url, summary, themes
- [ ] Executives sorted by activity (most recent posts first)
- [ ] Empty result if no new posts since last digest

**Ref:** SPEC.md FR-10 (Email Digest structure)

---

### P1-11: MJML Email Template

**Task:** Create the Phase 1 email digest template in MJML.

**Files to create:**
- `src/snd/templates/digest.mjml` — MJML template with:
  - Header: "Strategic Narrative Diff — Intelligence Digest"
  - Date range: "Posts from {start_date} to {end_date}"
  - Executive cards section (loop):
    - Thumbnail image (48×48, rounded)
    - Executive name + organization
    - For each recent post: title (linked), summary (2-3 sentences), theme tags
  - Footer: "Tracking {n} executives | Next digest: {date}"
  - Responsive: works at 600px and 320px
  - Color scheme: clean white/gray with blue accent (#007BFF)

**Acceptance Criteria:**
- [ ] MJML compiles to valid HTML without errors
- [ ] Template has placeholder variables for all dynamic content
- [ ] Renders correctly at 600px (desktop) and 320px (mobile)
- [ ] All sections present: header, executive cards, footer
- [ ] Links are clickable and use `{url}` placeholders

**Ref:** SPEC.md Section 14.2 (MJML skeleton), FR-10

---

### P1-12: SendGrid Email Sender

**Task:** Implement email rendering (MJML → HTML) and sending via SendGrid.

**Files to create:**
- `src/snd/services/email.py` — `EmailService` class:
  - `async def send_digest(content: DigestContent, config: AppConfig) -> bool`
  - Render MJML template with digest data → HTML string
  - Generate plain text fallback (strip HTML, preserve structure)
  - Send via SendGrid API to all configured recipients
  - Record digest in database (`digests` table) with `status='sent'`
  - Handle SendGrid errors: retry 3x, then mark digest as 'failed'
  - Structured logging: log recipient count, email size, delivery status

**Acceptance Criteria:**
- [ ] MJML template renders to valid HTML with real data
- [ ] Plain text fallback contains all key information (titles, URLs)
- [ ] Email sent successfully via SendGrid API (verified in SendGrid dashboard)
- [ ] Digest record created in database with correct status
- [ ] SendGrid failure handled gracefully (logged, digest marked 'failed')

**Ref:** SPEC.md FR-10, Section 8 (SendGrid in tech stack)

---

### P1-13: APScheduler Setup

**Task:** Configure APScheduler with two recurring jobs: collection (6h) and digest (Mon/Thu).

**Files to create/modify:**
- `src/snd/main.py` — (update stub):
  - Initialize APScheduler
  - Add job: `collection_pipeline.run()` — interval trigger, every 6 hours
  - Add job: `digest_pipeline.run()` — cron trigger, from `config.schedule.cron` + `config.schedule.timezone`
  - Jobs use async execution
  - Graceful error handling: job failures logged, don't crash the scheduler

**Acceptance Criteria:**
- [ ] Collection job runs automatically every 6 hours
- [ ] Digest job runs on configured schedule (default: Mon/Thu 8:00 AM JST)
- [ ] Job failures are logged but don't stop the scheduler
- [ ] Schedule is configurable via config.yaml
- [ ] Jobs can be triggered manually for testing

**Ref:** SPEC.md Section 7.1, 7.2 (pipeline triggers)

---

### P1-14: Application Entrypoint

**Task:** Create the main application entrypoint that ties everything together.

**Files to create/modify:**
- `src/snd/main.py` — complete implementation:
  - Load config from `config.yaml` (with env var overrides)
  - Initialize structlog (JSON format in production, human-readable in dev)
  - Initialize database connection (test connection on startup)
  - Run Alembic migrations on startup (optional, configurable)
  - Initialize APScheduler with collection + digest jobs
  - Run initial collection on startup (if database is empty)
  - Handle SIGINT/SIGTERM for graceful shutdown
  - Log startup banner with: version, exec count, schedule, database status

**Acceptance Criteria:**
- [ ] `python -m snd.main` starts the application
- [ ] Config loaded and validated on startup
- [ ] Database connection tested on startup (fails fast if unavailable)
- [ ] Scheduler starts with both jobs registered
- [ ] Ctrl+C triggers graceful shutdown (scheduler stopped, connections closed)
- [ ] Startup log shows: number of executives, next collection time, next digest time

**Ref:** SPEC.md Section 7 (Data Flow), Section 8 (Technology Stack)

---

### P1-15: Seed Data + Smoke Test

**Task:** Create an example config with real sources and a basic smoke test.

**Files to create:**
- `config.yaml` — (update) with 3 real, scrapable sources:
  1. NEC Corporate Blog: `https://jpn.nec.com/corporateblog/index.html`
  2. Google Japan Blog: `https://blog.google/intl/ja-jp/`
  3. Salesforce Japan Blog: `https://www.salesforce.com/jp/blog/recent-stories/`
- `tests/test_smoke.py` — basic end-to-end smoke test:
  - Load config → validate
  - Connect to database
  - Run collection pipeline once (with VCR recording or live)
  - Verify posts were stored
  - Run digest assembly
  - Verify digest content is non-empty
  - (Optional: render email, verify HTML is valid)

**Acceptance Criteria:**
- [ ] `config.yaml` contains 3 real executive sources
- [ ] Smoke test passes end-to-end (config → collect → store → assemble)
- [ ] At least 1 post collected from each source
- [ ] Digest content contains at least 1 executive card with posts
- [ ] No unhandled exceptions during the smoke test

**Ref:** SPEC.md Phase 1 Definition of Done (Section 24)

---

## Phase 1 Definition of Done (from SPEC.md)

When all 15 issues are merged:

- [ ] Email digest sent with ≥ 5 executive summaries
- [ ] All links in email resolve to correct blog posts
- [ ] Thumbnails display for posts that have og:image
- [ ] Total generation time < 3 minutes
- [ ] Collection runs automatically every 6 hours without errors
