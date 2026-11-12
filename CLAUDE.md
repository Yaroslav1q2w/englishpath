# EnglishPath

Платформа для самостійного вивчення англійської українською (A1 → B2).

- docs/decisions.md — технічні рішення і чому.
- docs/lesson-format.md — формат JSON-уроку (з'явиться разом зі схемою уроку).

## Стек

- `frontend/`: React 19 + TypeScript (strict), Vite, oxlint, Prettier
- `backend/`: Python 3.13, FastAPI, uv, ruff, mypy (strict), pytest
- Далі: PostgreSQL, SQLAlchemy 2.0 (спершу sync), Alembic, Redis, Docker, S3, LLM API

## Структура

- `frontend/src/` — FSD: `app/`, `pages/`, `widgets/`, `features/`, `entities/`, `shared/`. Шар створюємо, коли в ньому з'являється код. Імпорти через `@/`.
- `backend/app/` — FastAPI-застосунок; з появою бази — шари router → service → repository.
- `backend/tests/` — pytest.
- `content/` — JSON-уроки (`content/a2/unit-01/lesson-01.json`).

## Правила

- Інтерфейс і пояснення для користувача — українською.
- Код, назви змінних і коміти — англійською.
- Типізація всюди (TypeScript strict, Python type hints, mypy strict).
- Кожен новий ендпоінт — з тестом pytest.
- Секрети лише в `.env`, ніколи в коді.

## Команди

Фронтенд (`cd frontend`):
- `npm run dev` — dev-сервер (http://localhost:5173)
- `npm run lint` / `npm run format` / `npm run typecheck` / `npm run build`

Бекенд (`cd backend`):
- `uv sync` — встановити залежності
- `uv run fastapi dev app/main.py` — dev-сервер (http://localhost:8000, документація API на /docs)
- `uv run pytest` — тести
- `uv run ruff check .` / `uv run ruff format .` / `uv run mypy app tests`
