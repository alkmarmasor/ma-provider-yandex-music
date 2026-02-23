---
applyTo: "**"
---

# Project Rules for GitHub Copilot

## Language & Runtime

- Python 3.12+
- All code must be compatible with `python_version = "3.12"` (mypy target)
- Package manager: [`uv`](https://docs.astral.sh/uv/)

## Code Style

- Linter / formatter: **ruff** (`ruff.toml`, line-length = 100, target = py312)
- Type checker: **mypy** (strict mode — see `pyproject.toml [tool.mypy]`)
- Spell checker: **codespell**
- Pre-commit hooks run all three; always pass `pre-commit run --all-files` before pushing
- Line endings: **LF** (enforced by ruff format)
- Docstrings: PEP 257 convention

## Testing

- Framework: **pytest** with `asyncio_mode = "auto"`
- Snapshot testing: **syrupy**
- Run unit tests: `pytest tests/ -m "not integration"`
- Run full suite: `pytest tests/`
- New or changed code must be covered by tests
- Do not remove or weaken existing tests

## Commits & Branches

Conventional Commits format:
```
feat: <description>
fix: <description>
chore: <description>
test: <description>
docs: <description>
```

Branch naming (kebab-case, 2–4 words):
```
feature/<description>
fix/<description>
chore/<description>
```

## Pull Requests

- Target branch: `dev` (not `main`)
- Fill in the PR template (`.github/PULL_REQUEST_TEMPLATE.md`)
- No secrets or credentials in commits

## Security

- Never commit tokens, OAuth secrets, or credentials
- `SECURITY.md` documents the responsible disclosure process
