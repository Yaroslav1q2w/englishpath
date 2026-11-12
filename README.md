# EnglishPath

A self-study platform for learning English in Ukrainian: a clear path from A1 to B2.
Open a lesson, finish it in 45–60 minutes, know the topic is done and what comes next.

> 🚧 Early development: project foundation is in place, the lesson player is next.

## Tech stack

| Part     | Technology                                                       |
| -------- | ---------------------------------------------------------------- |
| Frontend | React 19, TypeScript (strict), Vite                              |
| Backend  | Python 3.13, FastAPI, uv                                         |
| Quality  | oxlint, Prettier, ruff, mypy (strict), pytest                    |
| Planned  | PostgreSQL, SQLAlchemy 2.0, Alembic, Redis, Docker, S3, LLM API  |

## Project structure

```
frontend/   React SPA
backend/    FastAPI app and content scripts
content/    lesson JSON files
docs/       technical decisions, data formats
```

## Roadmap

- **v0.1** — lesson player without a backend: course map, words, grammar, reading, exercises, 80% pass rule
- **v0.2** — FastAPI + PostgreSQL: lessons API, accounts, saved progress, server-side answer checking
- **v0.3** — spaced repetition, audio (TTS) and background jobs, email reminders
- **v0.4** — Docker, CI/CD, cloud deploy with a custom domain, S3 for media
- **v0.5** — AI: translation checking with explanations in Ukrainian, lesson generation pipeline
- **v1.0** — public beta: onboarding, "Today" screen, PWA

## Getting started

Requirements: Node.js 24+, Python 3.13, [uv](https://docs.astral.sh/uv/).

```bash
# frontend → http://localhost:5173
cd frontend
npm install
npm run dev

# backend → http://localhost:8000, API docs at /docs
cd backend
uv sync
uv run fastapi dev app/main.py
```

## Commands

|            | `frontend/`         | `backend/`                       |
| ---------- | ------------------- | -------------------------------- |
| Dev server | `npm run dev`       | `uv run fastapi dev app/main.py` |
| Tests      | —                   | `uv run pytest`                  |
| Lint       | `npm run lint`      | `uv run ruff check .`            |
| Format     | `npm run format`    | `uv run ruff format .`           |
| Type check | `npm run typecheck` | `uv run mypy app tests`          |
| Build      | `npm run build`     | —                                |

## Docs (Ukrainian)

- [docs/decisions.md](docs/decisions.md) — technical decisions and why
