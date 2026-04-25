# Project Guidelines

## Mandatory Development Checklist
- [ ] Lint: `uv run ruff check .`
- [ ] Build: `uv sync`
- [ ] Test: `uv run pytest`

## Build And Run
- Start app: `uv run uvicorn app.main:app --reload --host 0.0.0.0 --port 8000`
- Open in external browser only: `"$BROWSER" http://localhost:8000`

## Architecture
- Routes and app startup: `app/main.py`
- Session orchestration: `app/game_service.py`
- Bingo rules and board logic: `app/game_logic.py`
- Models: `app/models.py`
- UI is server-rendered Jinja2 + HTMX partial swaps (not JSON APIs).

## Conventions
- Keep game logic deterministic and reusable; avoid duplicating rules in routes.
- Return rendered template fragments from routes for HTMX interactions.
- Preserve board rules: 5x5, center free square, `check_bingo` + `get_winning_square_ids`.
- Follow current test style (`TestClient`, route behavior, HTML fragment assertions).
- Reuse utility CSS in `app/static/css/app.css`; add utilities there if needed.

## Repo Docs
Link instead of duplicating guidance:
- Setup flow: `README.md`, `workshop/00-overview.md`, `workshop/01-setup.md`
- Contribution process: `CONTRIBUTING.md`
- Styling and design rules: `.github/instructions/css-utilities.instructions.md`, `.github/instructions/frontend-design.instructions.md`
