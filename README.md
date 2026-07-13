# portfolio-backend

FastAPI backend for [kieuthuytkt.com](https://kieuthuytkt.com) — REST API, PostgreSQL, and contact form handling.

Part of a two-repo portfolio project. The parent workspace (`portfolio/`) holds shared docs and Cursor rules; **this folder is the Git repo root** deployed to Render.

| | |
|---|---|
| **Frontend** | `portfolio-frontend` repo → Vercel |
| **System design** | [ARCHITECTURE.md](./ARCHITECTURE.md) · [../ARCHITECTURE.md](../ARCHITECTURE.md) |
| **Learning guides** | [docs/learning/](../docs/learning/) |

## Stack

- Python 3.11+
- FastAPI + Uvicorn
- Pydantic v2
- SQLAlchemy 2.0 + Alembic
- PostgreSQL (Neon in production)

## Prerequisites

- Python 3.11+
- PostgreSQL (local or [Neon](https://neon.tech) for dev)
- Frontend at `http://localhost:3000` when testing CORS (optional until integration)

## Local setup

```bash
cd portfolio-backend
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env        # then edit values
uvicorn app.main:app --reload
```

- API: http://localhost:8000  
- Swagger UI: http://localhost:8000/docs  
- Health check: http://localhost:8000/health  

> **Note:** Application code is built incrementally via [FEATURES.md](./FEATURES.md) (start with BE-01). If `requirements.txt` or `app/` are not present yet, follow [04-fastapi-setup.md](../docs/learning/04-fastapi-setup.md).

## Environment variables

Copy `.env.example` to `.env` (never commit `.env`):

| Variable | Description |
|----------|-------------|
| `DATABASE_URL` | PostgreSQL connection string |
| `CORS_ORIGINS` | Comma-separated allowed origins (e.g. `http://localhost:3000`) |

## API (planned)

| Method | Endpoint | Purpose |
|--------|----------|---------|
| GET | `/health` | Health check |
| GET | `/api/projects` | List projects |
| GET | `/api/projects/{id}` | Project detail |
| GET | `/api/experience` | List experience |
| GET | `/api/skills` | List skills |
| POST | `/api/contact` | Submit contact form |

See [ARCHITECTURE.md](./ARCHITECTURE.md) and [../ARCHITECTURE.md](../ARCHITECTURE.md) for the full data model and request lifecycle.

## Project structure (target)

```
portfolio-backend/
  app/
    main.py             # FastAPI app, CORS, routers
    config.py           # settings from env
    deps.py             # DB session dependency
    models/             # SQLAlchemy models
    schemas/            # Pydantic schemas
    routers/            # projects, experience, skills, contact
  alembic/              # migrations
  tests/
```

## Tests

```bash
pytest
```

## Deploy

Hosted on **Render**. Set `DATABASE_URL` and `CORS_ORIGINS` (production frontend URL) in the Render dashboard.

## Development

- Feature tracker: [FEATURES.md](./FEATURES.md)
- Agent context: [AGENTS.md](./AGENTS.md)
- Worklog: [WORKLOG.md](./WORKLOG.md)
