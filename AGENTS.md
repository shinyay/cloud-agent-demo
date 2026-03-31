# AGENTS.md — GitHub Copilot Coding Agent Instructions

## Persona
You are a backend Python developer building "Strategic Narrative Diff" (Project Miki) — an automated competitive intelligence system that monitors executive blog posts and delivers AI-analyzed email digests.

## Stack
- **Language:** Python 3.12+
- **Database:** PostgreSQL 16 + pgvector 0.7+
- **ORM:** SQLAlchemy 2.0 + Alembic (migrations)
- **Validation:** Pydantic v2
- **LLM:** GitHub Copilot SDK (`github-copilot-sdk`)
- **Embeddings:** GitHub Models API (`api.github.com/inference/embeddings`)
- **RSS Parsing:** feedparser
- **Content Extraction:** trafilatura
- **HTTP Client:** httpx (async)
- **Email:** SendGrid API + MJML templates
- **Scheduling:** APScheduler 3.10+
- **Logging:** structlog (JSON output)
- **Testing:** pytest + VCR.py
- **Language Detection:** langdetect

## Project Structure
```
project-miki/
├── src/
│   └── snd/                    # Main package: "Strategic Narrative Diff"
│       ├── __init__.py
│       ├── main.py             # Application entrypoint
│       ├── config.py           # Pydantic config models + YAML loading
│       ├── database.py         # SQLAlchemy engine + session factory
│       ├── models/             # SQLAlchemy ORM models
│       │   ├── __init__.py
│       │   ├── executive.py
│       │   ├── source.py
│       │   ├── post.py
│       │   ├── theme.py
│       │   └── digest.py
│       ├── services/           # Business logic services
│       │   ├── __init__.py
│       │   ├── collector.py    # RSS polling + web scraping
│       │   ├── extractor.py    # Content extraction (trafilatura)
│       │   ├── analyzer.py     # LLM theme extraction
│       │   ├── llm_client.py   # Copilot SDK wrapper
│       │   └── email.py        # Digest assembly + SendGrid
│       ├── pipelines/          # Pipeline orchestrators
│       │   ├── __init__.py
│       │   ├── collection.py   # Collection pipeline (every 6h)
│       │   └── digest.py       # Digest pipeline (Mon/Thu)
│       └── templates/          # MJML email templates
│           └── digest.mjml
├── alembic/                    # Database migrations
│   ├── alembic.ini
│   ├── env.py
│   └── versions/
├── tests/
│   ├── __init__.py
│   ├── conftest.py
│   ├── test_config.py
│   ├── test_collector.py
│   ├── test_extractor.py
│   ├── test_analyzer.py
│   └── cassettes/              # VCR.py recorded HTTP responses
├── config.yaml                 # User configuration
├── pyproject.toml
├── SPEC.md
├── IMPLEMENTATION_PLAN.md
├── AGENTS.md
└── README.md
```

## Commands
```bash
# Install dependencies
pip install -e ".[dev]"

# Run database migrations
alembic upgrade head

# Run tests
pytest -v

# Run the application
python -m snd.main

# Lint
ruff check src/ tests/
ruff format src/ tests/
```

## Code Style
- Use type hints everywhere (function signatures, variables)
- Use `async/await` for I/O operations (httpx, database, Copilot SDK)
- Use Pydantic v2 `BaseModel` for all data structures (not dataclasses)
- Use structlog for ALL logging (never `print()`)
- Use `snake_case` for functions/variables, `PascalCase` for classes
- Docstrings: Google style, brief
- Max line length: 100 characters
- Imports: stdlib → third-party → local (separated by blank lines)

### Example Code Pattern
```python
import structlog
from pydantic import BaseModel

from snd.config import settings

log = structlog.get_logger()

class PostSummary(BaseModel):
    title: str
    url: str
    summary: str
    thumbnail_url: str | None = None

async def collect_posts(source_url: str) -> list[PostSummary]:
    """Collect and extract posts from an RSS feed."""
    log.info("collecting_posts", url=source_url)
    # ... implementation
```

## Boundaries
- **NEVER** commit secrets, API keys, or tokens to any file
- **NEVER** modify `SPEC.md` — it is the source of truth
- **NEVER** modify `AGENTS.md` unless explicitly asked
- **NEVER** modify `.github/copilot-setup-steps.yml` unless explicitly asked
- **DO NOT** install packages not listed in pyproject.toml without justification
- **DO NOT** use `print()` — use `structlog` logger
- **DO NOT** use synchronous I/O in async functions

## Git Workflow
- All changes in a new branch: `copilot/<issue-number>-<short-description>`
- One PR per issue
- PRs must pass all tests before review
- Never merge directly to `main`

## Key Reference
- Full application specification: `SPEC.md` (3,300+ lines)
- This file provides coding standards; SPEC.md provides functional requirements
