# design-engineering
## Monorepo layout
- `frontend/` – UI app (React/Streamlit)
- `backend/` – FastAPI services & APIs
- `shared/` – shared modules/assets (optional)

## Branching model
- `main` – protected, production-ready
- `dev` – integration branch
- Feature work happens on forks → PR → `dev`

## Conventions
- Folders/files: `kebab-case` (e.g., `submission-service`)
- Python: modules `snake_case.py`, classes `PascalCase`
- JS/TS: files `kebab-case`, variables `camelCase`

See `CONTRIBUTING.md` for workflow & PR rules.