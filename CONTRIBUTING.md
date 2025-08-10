# Contributing

## Branching
- Only `main` and `dev` exist in upstream.
- All contributors work on **forks**:
  - Feature branches: `feature/<short-name>`
  - Fix branches: `fix/<short-name>`
  - Docs branches: `docs/<short-name>`

## PR Rules
- Target branch: `dev`
- Mark WIP PRs with `WIP:` prefix or draft PRs
- Tag **at least 2 reviewers** before merge
- Link issue(s) and add a brief summary + test notes

## Naming Conventions
- Folders/files: `kebab-case`
- Python: `snake_case` for files/functions; `PascalCase` classes
- JS/TS: `kebab-case` files; `camelCase` vars; `PascalCase` components

## Commits
- Conventional style (recommended):
  - `feat: …`, `fix: …`, `docs: …`, `refactor: …`, `test: …`, `chore: …`

## Frontend vs Backend
- Frontend code → `frontend/`
- Backend code → `backend/`
- Shared code/assets only if truly reused → `shared/`
