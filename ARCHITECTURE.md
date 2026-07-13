# Backend Architecture

System context: [../ARCHITECTURE.md](../ARCHITECTURE.md)

## Structure (planned)

```
portfolio-backend/
  app/
    main.py             # FastAPI app, CORS, router includes
    deps.py             # get_db dependency
    config.py           # settings from env
    models/             # SQLAlchemy models
    schemas/            # Pydantic request/response
    routers/
      projects.py
      experience.py
      skills.py
      contact.py
  alembic/              # migrations
  tests/
```

## Layers

1. **Routers** — HTTP endpoints, call services/CRUD, return schemas
2. **Schemas** — Pydantic validation (in/out)
3. **Models** — SQLAlchemy ORM (`Mapped`, relationships)
4. **Deps** — DB session per request, settings injection

## API design

- Prefix: `/api/` for resource routes, `/health` for health check
- Read endpoints: public
- POST `/api/contact`: validate body, persist, return 201
- CORS: allow frontend origin(s) from env

## Database

- PostgreSQL via `DATABASE_URL`
- Alembic for migrations; seed script for portfolio content
- Neon in production

## Error handling

- 404 for missing resources
- 422 for validation errors (Pydantic automatic)
- 500 logged server-side; generic message to client
