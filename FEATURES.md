# Backend Features

Parent rollup: [../docs/FEATURES.md](../docs/FEATURES.md) · Guide index: [../docs/learning/](../docs/learning/)

**Status:** `Todo` | `In progress` | `Blocked` | `In review` | `Done`  
**Rule:** One `In progress` at a time. Not `Done` until validation passes.

| ID | Title | Owner | Status | Validation | Guide |
|----|-------|-------|--------|------------|-------|
| BE-01 | FastAPI project setup + health route | You | Todo | `/health` returns 200; Swagger at `/docs` | [04-fastapi](../docs/learning/04-fastapi-setup.md) |
| BE-02 | SQLAlchemy models | You | Todo | Models import without error | [05-models](../docs/learning/05-sqlalchemy-models.md) |
| BE-03 | Pydantic schemas | You | Todo | Schemas validate sample payloads | [06-schemas](../docs/learning/06-pydantic-schemas.md) |
| BE-04 | CRUD routes + CORS + contact POST | You | Todo | `pytest` passes; CORS allows localhost:3000 | [07-routes](../docs/learning/07-routes-and-crud.md) |
| BE-05 | Alembic migrations + seed | You | Todo | `alembic upgrade head` + seed populates DB | [08-alembic](../docs/learning/08-alembic-postgres.md) |

## Cross-repo links

- BE-04 + FE-04 → INT-01 (integration)
- BE-02 → BE-03 → BE-04 → BE-05 (sequential)
