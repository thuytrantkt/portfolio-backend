# Backend — Agent Context

Parent: [../AGENTS.md](../AGENTS.md) · Architecture: [ARCHITECTURE.md](./ARCHITECTURE.md)

## Stack

- Python 3.11+, FastAPI, Uvicorn, Pydantic v2
- SQLAlchemy 2.0, Alembic, PostgreSQL

## Run / test

```bash
cd portfolio-backend
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload   # http://localhost:8000
pytest
```

## Env vars

```bash
# .env (never commit)
DATABASE_URL=postgresql://user:pass@localhost:5432/portfolio
CORS_ORIGINS=http://localhost:3000
```

## Conventions

- Structure: `app/main.py`, `routers/`, `models/`, `schemas/`, `deps.py`
- SQLAlchemy 2.0 typed style: `Mapped[...]`, `mapped_column`
- Pydantic v2 for request/response schemas
- Dependency-injected DB sessions per request

## Task tracking

- Features: [FEATURES.md](./FEATURES.md)
- Worklog: [WORKLOG.md](./WORKLOG.md) — update on BE branches only
- Guides: [../docs/learning/](../docs/learning/)

## Session protocol

Follow [../AGENTS.md#session-protocol](../AGENTS.md#session-protocol). **BE scope:** log-out writes [FEATURES.md](./FEATURES.md) + [WORKLOG.md](./WORKLOG.md). Validation checks: `pytest`, `curl localhost:8000/health`.

## GitHub

Repo: `portfolio-backend` · Deploy: Render (repo root = this folder)
